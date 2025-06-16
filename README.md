# Electrical Connector Production Line Simulation  
**Built with Arena Simulation Software & SAP Crystal Reports**

## Project Description
This project, carried out during my BSc in Industrial Engineering, models the production process of electrical connectors using Arena software (Rockwell Automation). The simulation replicates the entire workflow: from order arrival and raw material preparation to final packaging. It aims to analyze and optimize performance indicators such as productivity, WIP, and lead time using SAP Crystal Reports.

![image](https://github.com/user-attachments/assets/5841bf8a-983f-423d-a8ea-b016e7ee6e0b)

---

## Production Workflow

### 1. Order Arrival
- Regular orders every hour: 60, 80, or 100 units  
- Unplanned orders (exp. interarrival time = 3h): 40, 60, or 80 units  
- All orders contain one product type  
- Product mix:  
  - 200A male: 30%  
  - 200A female: 30%  
  - 500A male: 20%  
  - 500A female: 20%
 
![image](https://github.com/user-attachments/assets/64cc7c6d-f048-46b8-9e2b-3e4e80c4efd7)

### 2. Preparation Station
- Operator prepares basettes (20 contacts each) from raw bags (150 pieces)  
- 1% of contacts are visually rejected and replaced  
- Full basettes (5 per cart) sent to gold-plating  
- Time examples:  
  - Prepare basette: `UNIF(0.5, 1)` min  
  - Process contact: `TRIA(7, 9, 12.5)` sec  
  - Move full cart: `UNIF(1.2, 2.5)` min

![image](https://github.com/user-attachments/assets/3d72f307-a787-4321-8653-cba37a49e1dc)


### 3. Gold-Plating Station
- Operator dips basettes into gold baths (2 available)  
- Bath refill every 50 basettes: `UNIF(20, 30)` min  
- Time examples:  
  - Dip basette: `TRIA(5, 7, 9)` sec  
  - Plating time: 8 min  
  - Remove basette: `TRIA(14, 16, 18)` sec  
- Full carts sent to pressing

![image](https://github.com/user-attachments/assets/5232cc71-68b7-432e-bac2-bc17d9283a82)


### 4. Pressing Station
- Operator inserts contacts and plastic shells into molds  
- 4 mold types (one per connector type); changeover: 5 min  
- Output stored in 20-unit boxes  
- Time examples:  
  - Load press: `TRIA(3.6, 4.5, 7)` sec  
  - Press cycle: 7 sec  
  - Unload: `TRIA(0.6, 1, 1.5)` sec


![image](https://github.com/user-attachments/assets/e0faede2-9bc8-48cc-8673-61d23971fc51)

### 5. Testing Station
- All connectors tested (100%)  
- Failure rate:  
  - 200A = 3%  
  - 500A = 2%  
- Defects logged: `UNIF(60, 120)` sec  
- Good units stored by type

![image](https://github.com/user-attachments/assets/c94fd7a6-4559-4d2c-99ab-0a5a3b3dc5b7)


### 6. Packaging Station
- 200A: Bags of 30 units  
- 500A: Bags of 20 units  
- Single heat-sealing machine (shared among operators)  
- Sealer MTBF = 3h, MTTR = 15 min (exponential)  
- Time examples:  
  - Prep bag: `TRIA(3, 7, 25)` sec  
  - Pack 200A: `TRIA(4, 5.5, 7)` min  
  - Pack 500A: `TRIA(7, 9, 12)` min  
  - Seal: `UNIF(20, 35)` sec
 
![image](https://github.com/user-attachments/assets/0d6a4ec9-5b92-42b4-b635-68212ea3d59e)

---

## Simulation Settings
- Simulated period: 20 working days  
- Working time: 2 shifts per day, 8 hours each  
- Each station may have multiple operators  
- Pressing: 1 press per operator  
- Model supports organizational improvement suggestions

---

## Simulation Goals

1. Determine optimal number of operators per station  
2. Define required number of basette carts  
3. Evaluate performance metrics:  
   - Productivity  
   - Work-In-Progress (WIP)  
   - Lead Time

