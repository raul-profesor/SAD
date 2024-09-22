Certainly! Below is a similar exercise, but this time with **hints** to guide students on how to make decisions about UPS selection, power consumption, and cybersecurity considerations.

---

### **Guided Exercise: Choosing the Right UPS for Critical Systems**

#### **Objective:**
Students will assess power requirements and select the appropriate UPS for critical systems in a scenario. They will be provided with hints to guide them in choosing the correct UPS models, calculating runtime, and considering redundancy and cybersecurity measures.

---

### **Scenario:**

You are the IT administrator for a mid-sized company with several critical systems. Due to frequent power outages, you’ve been tasked with choosing a UPS system to keep these systems operational for the necessary amount of time.

#### **Critical Systems:**

| **System**                | **Power Consumption (Watts)** | **Priority Level** | **Required Uptime** |
|----------------------------|-------------------------------|--------------------|---------------------|
| Database Server            | 800 W                         | High               | 30 minutes          |
| Web Server                 | 600 W                         | High               | 15 minutes          |
| Firewall                   | 100 W                         | Medium             | 15 minutes          |
| Network Switch             | 80 W                          | Medium             | 15 minutes          |
| Workstation (x5)           | 200 W each                    | Low                | 10 minutes          |
| CCTV System (Cameras & NVR)| 400 W                         | Medium             | 1 hour              |
| Backup NAS                 | 300 W                         | Low                | 10 minutes          |

---

### **Task:**
Your goal is to choose the appropriate UPS model(s) that can handle the power consumption and ensure that each system has the required runtime. You should also consider redundancy for high-priority systems and address cybersecurity concerns regarding UPS management.

### **Steps and Hints:**

---

#### **Step 1: Calculate Total Power Consumption**

**Hint:**  
The total power consumption is the sum of the power draw from all systems. Make sure to include all systems in your calculation. The power consumption is given in watts.

\$
\text{Total Power Consumption (Watts)} = 800 \, (\text{DB Server}) + 600 \, (\text{Web Server}) + \dots
\$

---

#### **Step 2: Convert Power Consumption to UPS Capacity (VA)**

**Hint:**  
UPS systems are typically rated in **Volt-Amps (VA)**. To convert the total power in **Watts** to **VA**, use the following formula:

\[
\text{UPS Capacity (VA)} = \frac{\text{Total Power (Watts)}}{\text{Power Factor}}
\]

Where the **Power Factor** is generally 0.8 for most UPS units. This conversion is necessary because UPS systems account for reactive power, which is why VA and watts differ.

For example, if you calculate the total power to be 3280 W, the VA requirement would be:

\[
\text{UPS Capacity (VA)} = \frac{3280}{0.8} = 4100 \, \text{VA}
\]

---

#### **Step 3: Calculate UPS Runtime for Each System**

**Hint:**  
Most UPS datasheets provide **runtime curves or tables** showing how long the UPS can support a specific load. If you know the power load in watts and the UPS capacity, use these resources to determine how long the UPS will provide backup power.

For example, if a UPS can handle a 2400 W load and the runtime at full load is 9 minutes, and your system only uses 1200 W (50% of the capacity), the runtime will be longer—around **27 minutes** according to the data.

You can also use the simplified formula to approximate runtime:

\[
\text{UPS Runtime (minutes)} = \frac{\text{UPS Capacity (Wh)}}{\text{System Load (Watts)}}
\]

---

#### **Step 4: Divide Systems by Priority**

**Hint:**  
Not all systems need the same uptime. Group systems by **priority level** to better allocate UPS resources. Critical systems like the **Database Server** and **Web Server** should have longer runtimes and possibly redundancy, while lower-priority systems can have shorter runtimes.

- **High-Priority Systems** (Database Server, Web Server): Need 15–30 minutes of uptime.
- **Medium-Priority Systems** (Firewall, Network Switch, CCTV): Need 15 minutes to 1 hour of uptime.
- **Low-Priority Systems** (Workstations, Backup NAS): Need only 10 minutes for safe shutdown.

---

#### **Step 5: Select Appropriate UPS Models**

**Hint:**  
Use the table below to help you choose the right UPS for each group of systems based on their power requirements and runtime needs. Consider whether you need to purchase multiple UPS units or a larger one to cover all systems.

| **UPS Model**        | **Capacity (VA)** | **Power Factor** | **Max Load (Watts)** | **Runtime at Full Load (Minutes)** | **Runtime at 50% Load (Minutes)** | **Price** |
|----------------------|-------------------|------------------|----------------------|------------------------------------|-----------------------------------|-----------|
| APC Smart-UPS 1500VA  | 1500              | 0.8              | 1200                 | 4                                  | 14                                | $500      |
| Eaton 5P 2200VA       | 2200              | 0.9              | 1980                 | 7                                  | 18                                | $900      |
| CyberPower 3000VA     | 3000              | 0.8              | 2400                 | 9                                  | 27                                | $1,200    |

- **Hint 1:** Start by checking if a single UPS can handle the entire power load. For example, if the total power is 3280 W, a **4100 VA UPS** would be required.
- **Hint 2:** If no single UPS can provide the required runtime for all systems, split the load into multiple UPS systems, grouping by priority level.
- **Hint 3:** Look at **runtime curves** in datasheets to check how long each UPS will support the systems at full and partial loads.

---

#### **Step 6: Consider Redundancy and Cybersecurity**

**Hint:**  
For **high-priority systems** (e.g., Database Server, Web Server), consider implementing **redundancy** by using two UPS units. Redundancy ensures that if one UPS fails, the second unit can take over, keeping the system operational.

Also, ensure that the UPS supports **remote monitoring** (via SNMP or web-based interfaces) so you can receive alerts and monitor battery health. Make sure these management features are **secured**, including using strong passwords, disabling unnecessary services, and encrypting communication between the UPS and monitoring systems.

---

### **Questions to Answer in Your Report:**

1. **Total Power Consumption:** What is the total power consumption for all systems?
   - **Hint:** Sum up the power (in watts) of all the systems.
   
2. **UPS Capacity:** What is the total UPS capacity (in VA) required for all systems?
   - **Hint:** Use the formula and a power factor of 0.8 to convert watts to VA.

3. **UPS Selection:** Which UPS model(s) did you choose, and why?
   - **Hint:** Consider runtime, load, and price when selecting the UPS.

4. **Redundancy:** Did you include any redundancy for high-priority systems? Why or why not?
   - **Hint:** Redundancy can prevent downtime in case of UPS failure.

5. **Cybersecurity Considerations:** What security measures will you take to ensure the UPS management interface is secured?

---

### **Solution Outline:**

Here’s how you would approach the solution based on the steps and hints provided:

1. **Total Power Consumption:**
   - Add up the power consumption of all systems:
   \[
   800 + 600 + 100 + 80 + 1000 + 400 + 300 = 3280 \, \text{W}
   \]

2. **Convert to VA:**
   - Using a power factor of 0.8:
   \[
   \text{UPS Capacity (VA)} = \frac{3280}{0.8} = 4100 \, \text{VA}
   \]

3. **Select UPS Models:**
   - You need a total of 4100 VA to support all systems.
   - For **high-priority systems** (1400 W), use two **CyberPower 3000VA** units to ensure 30 minutes of uptime with redundancy.
   - For **medium-priority systems** (580 W), use an **Eaton 5P 2200VA** unit, which provides more than 1 hour of runtime at 30% load.
   - For **low-priority systems** (1300 W), two **APC Smart-UPS 1500VA** units will handle the load and provide around 10–15 minutes of runtime.

4. **Redundancy:**
   - Redundancy is provided for **high-priority systems** by using two **CyberPower 3000VA** UPS units. If one fails, the other can continue to support the systems.

5. **Cybersecurity Considerations:**
   - Ensure **remote monitoring** is enabled for the UPS, secure the management interfaces with strong passwords, and restrict network access to the UPS.
   - Use **encryption** for communications (e.g., SNMPv3 or HTTPS) between the UPS and monitoring software.

---

### **Final Deliverable:**
- A report that includes:
  1.