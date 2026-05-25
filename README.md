<h1>ExpNo 1 :Developing AI Agent with PEAS Description</h1>
<h3>Name: NANDHIKA P</h3>
<h3>Register Number: 212223040125 </h3>


<h3>AIM:</h3>
<br>
<p>To find the PEAS description for the given AI problem and develop an AI agent.</p>
<br>
<h3>Theory</h3>
<h3>Medicine prescribing agent:</h3>
<p>Such this agent prescribes medicine for fever (greater than 98.5 degrees) which we consider here as unhealthy, by the user temperature input, and another environment is rooms in the hospital (two rooms). This agent has to consider two factors one is room location and an unhealthy patient in a random room, the agent has to move from one room to another to check and treat the unhealthy person. The performance of the agent is calculated by incrementing performance and each time after treating in one room again it has to check another room so that the movement causes the agent to reduce its performance. Hence, agents prescribe medicine to unhealthy.</p>
<hr>
<h3>PEAS DESCRIPTION:</h3>
<table>
  <tr>
    <td><strong>Agent Type</strong></td>
    <td><strong>Performance</strong></td>
     <td><strong>Environment</strong></td>
    <td><strong>Actuators</strong></td>
    <td><strong>Sensors</strong></td>
  </tr>
    <tr>
    <td><strong>Medicine prescribing agent</strong></td>
    <td><strong>Treating unhealthy, agent movement</strong></td>
     <td><strong>Rooms, Patient</strong></td>
    <td><strong>Medicine, Treatment</strong></td>
    <td><strong>Location, Temperature of patient</strong></td>
  </tr>
</table>
<hr>
<H3>DESIGN STEPS</H3>
<h3>STEP 1:Identifying the input:</h3>
<p>Temperature from patients, Location.</p>
<h3>STEP 2:Identifying the output:</h3>
<p>Prescribe medicine if the patient in a random has a fever.</p>
<h3>STEP 3:Developing the PEAS description:</h3>
<p>PEAS description is developed by the performance, environment, actuators, and sensors in an agent.</p>
<h3>STEP 4:Implementing the AI agent:</h3>
<p>Treat unhealthy patients in each room. And check for the unhealthy patients in random room</p>
<h3>STEP 5:</h3>
<p>Measure the performance parameters: For each treatment performance incremented, for each movement performance decremented</p>

<h2>Program</h2>

```
import random
import time

class SecurityAgent:
    def __init__(self, zones):
        self.zones = zones
        
        self.performance = 100
        
        self.risk_scores = {zone: 1 for zone in zones}
        
        self.history = []

    def sense_environment(self, zone):
        """
        Simulate real-world probability of suspicious activity
        """
        probability = random.uniform(0, 1)

        threshold = 0.6 - (self.risk_scores[zone] * 0.05)
        return probability > threshold

    def choose_zone(self):
        """
        Choose zone with highest risk score
        """
        return max(self.risk_scores, key=self.risk_scores.get)

    def act(self, zone, detected):
        """
        Take action based on detection
        """
        print(f"\nScanning {zone}...")
        time.sleep(1)

        if detected:
            print(f"⚠ Suspicious activity detected in {zone}!")
            print("Alert triggered!")
            self.performance += 20
            self.risk_scores[zone] += 2

        else:
            print(f"No suspicious activity in {zone}.")

            # Chance of false assumption
            if random.choice([True, False]):
                print("Missed suspicious activity!")
                self.performance -= 5
                self.risk_scores[zone] += 1
            else:
                self.performance -= 1
                self.risk_scores[zone] = max(1, self.risk_scores[zone] - 1)

        self.performance -= 1

        self.history.append((zone, detected))

        print(f"Updated Risk Scores: {self.risk_scores}")
        print(f"Current Performance: {self.performance}")

    def run(self, cycles=8):
        for _ in range(cycles):
            zone = self.choose_zone()
            detected = self.sense_environment(zone)
            self.act(zone, detected)

        print("\n=== FINAL REPORT ===")
        print("Final Performance:", self.performance)
        print("Detection History:", self.history)

zones = ["Zone A", "Zone B", "Zone C", "Zone D"]

agent = SecurityAgent(zones)

agent.run()
```

<h2>Output</h2>

<img width="1231" height="530" alt="image" src="https://github.com/user-attachments/assets/15981582-446a-4e58-a7cb-f1e7d5288b1b" />

<h2>Result</h2>
Thus, to find the PEAS description for the given AI problem and develop an AI agent is executed successfully.


