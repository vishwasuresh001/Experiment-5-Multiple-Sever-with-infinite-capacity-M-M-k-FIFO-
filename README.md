# Experiment-5-Multiple-Sever-with-infinite-capacity-(M/M/k)-(oo/FIFO)
# Aim
 	To find 
  
a)	Average number of materials in the system 

b)	Average number of materials in the conveyor

c)	Waiting time of each material in the system 

d)	Waiting time of each material in the conveyor

If the arrival of materials follow poisson process with mean interval time 10 seconds, service time of two lather machine follow exponential distribution with mean sevice time 1 second and average service time of robot is 7 seconds.

# Software required: Visual Components and Python
# Theory: 
Queueing shows up everywhere: cafeterias, libraries, banks—anywhere arrivals need service and may face delay. Waiting can’t be removed entirely, but it can be controlled. Adding more servers reduces delays, though it may increase idle time.
In an M/M/∞ system, there are infinitely many servers, so every arrival begins service immediately and no one waits. Arrivals follow a Poisson rate λ, and each server provides exponential service with rate μ.
If there are k customers in the system, then k servers are busy. Each works independently, so the total service-completion rate is the minimum of k exponential clocks, giving an overall departure rate of kμ.
This lets us treat the M/M/∞ model as a simple Markov chain and find the distribution of the number of customers in service.
# Algorithm
<img width="806" height="297" alt="image" src="https://github.com/user-attachments/assets/e08285b0-8d2d-4b63-8e52-4bf2d065b0ff" />

# Program
```
#exo no:5
import math 

arr_time_input = '' 
while not arr_time_input.strip():  # Loop until a non-empty input is received 
    arr_time_input = input("Enter the mean inter arrival time of objects from feeder (in secs):") 
    if not arr_time_input.strip(): 
        print("Input cannot be empty. Please enter a value.") 

arr_time = float(arr_time_input) 
ser_time = float(input("Enter the mean inter service time of lathe machine (in secs):")) 
Robot_time = float(input("Enter the Additional time taken for the robot (in secs):")) 
c = int(input("Number of service centres:")) 

lam = 1 / arr_time 
mu = 1 / (ser_time + Robot_time) 

print("------------------------------------------------") 
print("Multiple Server with infinite capacity- (M/M/c):(00/FIFO)") 
print("----------------------------------------------------") 
print("The mean arrival rate per second: %0.2f" % lam) 
print("The mean service rate per second: %0.2f" % mu) 

rho = lam / (c * mu) 

sum = (lam / mu)**c * (1 / (1 - rho)) / math.factorial(c) 

for i in range(0, c): 
    sum = sum + (lam / mu)**i / math.factorial(i) 

P0 = 1 / sum 

if (rho < 1): 
    Lq = (P0 / math.factorial(c)) * (1 / c) * (lam / mu)**(c + 1) / (1 - rho)**2 
    Ls = Lq + lam / mu 
    Ws = Ls / lam 
    Wq = Lq / lam 
    print("Average number of objects in the system: %0.2f" % Ls) 
    print("Average numner of objects in the conveyor: %0.2f" % Lq) 
    print("Average waiting time of an object in the system: %0.2f secs" % Ws) 
    print("Average waiting time of an object in the conveyor: %0.2f secs" % Ws) 
    print("Probability that the system is busy: %0.2f" % (rho)) 
    print("Probability that the system is empty:%0.2f " % (1 - rho)) 

else: 
    print("Warning! Objects overflow will happen in the conveyor") 
    print("-----------------------------------------------------")
```
# colab link
https://colab.research.google.com/drive/19DJaM1HeTKNcrANuBYJO55ORteGK5JOR?usp=sharing

# Output
<img width="843" height="336" alt="Screenshot 2025-12-11 211441" src="https://github.com/user-attachments/assets/ea587f39-5852-4287-9e45-7905e5d4bbed" />

# Result
       The average number of material in the system and in the conveyor and waiting are  successfully found.

