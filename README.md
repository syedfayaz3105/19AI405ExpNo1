<h1>ExpNo 1 :Developing AI Agent with PEAS Description</h1>
<h3>Name: Farhana H</h3>
<h3>Register Number: 212223230057 </h3>

<h3>AIM:</h3>
<br>

<p>To find the PEAS description for the given AI problem and develop an AI agent.</p>

<h3>Theory</h3>
<h3>AI Surveillance System Agent:</h3>
<p>
This agent monitors a restricted area using cameras and detects suspicious activity such as unauthorized entry or unusual movement. The environment consists of multiple zones (e.g., Zone A and Zone B). The agent continuously scans both zones.

If suspicious activity is detected in any zone, the agent raises an alert. The agent's performance improves when it correctly detects threats and decreases when it wastes time scanning empty zones or misses detection.

The agent uses sensors like cameras and motion detectors to observe activity and actuators such as alarms and notifications to respond..</p>
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
    <td><strong>AI Surveillance System</strong></td>
    <td><strong>Accurate threat detection, minimal false alarms</strong></td>
     <td><strong>Monitored zones, people movement</strong></td>
    <td><strong>Alarm, alert system</strong></td>
    <td><strong>Cameras, motion sensors</strong></td>
  </tr>
</table>
<hr>
<H3>DESIGN STEPS</H3>
<h3>STEP 1:Identifying the input:</h3>
<p>Motion detection status (Yes/No)</p>
<p>Zone location (Zone A / Zone B)</p>
<h3>STEP 2:Identifying the output:</h3>
<p>Trigger alert if suspicious activity is detected.</p>
<h3>STEP 3:Developing the PEAS description:</h3>
<p>PEAS description is developed by identifying performance, environment, actuators, and sensors of the agent..</p>
<h3>STEP 4:Implementing the AI agent:</h3>
<p>Monitor both zones</p>
<p>Detect suspicious activity randomly</p>
<p>Raise alert if detected</p>
<h3>STEP 5:</h3>
<p>Increase performance for correct detection</p>
<p>Decrease performance for unnecessary scanning</p>

## Program
```python
import random
import time

class SurveillanceAgent:
    def __init__(self, zones):
        self.zones = zones
        self.performance = 0
        
        # Internal belief (risk score per zone)
        self.risk_scores = {zone: 1 for zone in zones}
        
        # Memory of detections
        self.history = []

    def sense_environment(self, zone):
        """
        Simulate real-world probability of suspicious activity
        """
        probability = random.uniform(0, 1)
        
        # Higher probability zones more likely to have activity
        threshold = 0.6 - (self.risk_scores[zone] * 0.05)
        return probability > threshold

    def choose_zone(self):
        """
        Choose zone with highest risk score (intelligent decision)
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
            self.risk_scores[zone] += 2  # Increase confidence
        else:
            print(f"No suspicious activity in {zone}.")
            
            # Chance of false assumption (missed detection simulation)
            if random.choice([True, False]):
                print("Missed suspicious activity!")
                self.performance -= 5
                self.risk_scores[zone] += 1
            else:
                self.performance -= 1
                self.risk_scores[zone] = max(1, self.risk_scores[zone] - 1)

        # Movement cost
        self.performance -= 1

        # Save history
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


# Create and run agent
zones = ["Zone A", "Zone B", "Zone C"]
agent = SurveillanceAgent(zones)
agent.run()
```

## Output

<img width="1506" height="807" alt="Screenshot 2026-04-27 101728" src="https://github.com/user-attachments/assets/d3590316-d49e-4c65-a967-5aac8fd99318" />

## Result 

The intelligent surveillance agent was successfully implemented. It used internal state (risk scores), probabilistic sensing, and adaptive decision-making to improve detection efficiency and overall performance.
