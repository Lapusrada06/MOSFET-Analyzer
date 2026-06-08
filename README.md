# MOSFET-Analyzer
Python program for MOSFET operating region and drain current analysis.

print(" MOSFET Analyzer ")

while True:
    
    print("\nEnter MOSFET Parameters")
    
    Vgs = float(input("Vgs (V) : "))
    Vth = float(input("Vth (V) : "))
    k = float(input("k value  : "))
    
    if Vgs <= Vth:
        region = "cutoff region"
        Id = 0
        
    else:
        region = "saturation region"
        Id =  k * ((Vgs - Vth) ** 2)
        
    print("\n========= RESULT =========")
    print("Operating Region :", region)
    print("Drain Current Id :", round(Id,4), "A")
    
    print("\n========= ANALYSIS =========")
    
    if Id == 0:
        print("MOSFRT is off")
        
    elif Id < 1:
        print("Low current")
        
    elif Id < 5:
        print("Medium current")
        
    else:
        print("High current")
    
    save = input("\nSave Result? (y/n): ")
    
    if save.lower() == "y":
        
        file = open("report.txt","a")
        
        file.write("\n")
        file.write("MOSFET ANALYSIS\n")
        file.write(f"Vgs = {Vgs}\n")
        file.write(f"Vth = {Vth}\n")
        file.write(f"k = {k}\n")
        file.write(f"Region = {Region}\n")
        file.write(f"Id = {Id}\n")
        file.write(------------------"\n")
        
        file.closed()
        
        print("Save to report.txt")
        
    again = input("\nAnalyze another MOSFET? (y/n): ")
    
    if again.lower() != "y":
        break
    
    print("\nProgram Finished")
        
        
