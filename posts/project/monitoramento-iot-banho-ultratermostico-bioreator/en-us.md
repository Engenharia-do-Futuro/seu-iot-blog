![Cover](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/images/seuiot_common/Capa.png)

# IoT Monitoring of the Ultratermostatic Bath in a Bioreactor: Context, Problem, and Solution

---

## The Context: Cell Culture and the Role of Temperature

Biotechnology laboratories working with cell culture operate in an environment where any variation in conditions can compromise weeks or months of work. Cell cultivation — whether bacterial, fungal, or mammalian — requires strict control of temperature, pH, oxygenation, and nutrients. Any deviation outside tolerable ranges can mean cell death, complete batch loss, or even damage to equipment.

In 3D cell culture, or in fermentative processes, the bioreactor can be the heart of this process. It is a piece of equipment designed to create ideal conditions for cells or microorganisms to multiply in a controlled manner. This equipment can operate continuously, often for hours or consecutive days, depending on the process being carried out.

To maintain a stable internal temperature in the bioreactor, a **temperature jacket** system is used — an external chamber surrounding the reactor vessel through which heated or cooled water circulates. This water can be supplied by an external device — the **ultratermostatic bath** — or by the water supply line. Using baths is usually the recommended approach, as it ensures greater control over the flow, quality, and temperature of the water reaching the equipment.

![Microbiology and Bacteriophage Laboratory — NB2 Biosafety Area](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/project/monitoramento-iot-banho-ultratermostico-bioreator/images/laboratory_view.gif)

---

## The Process: How the Ultratermostatic Bath Works

The ultratermostatic bath — in the documented case, the **NT 281 model from Novatécnica** — is responsible for maintaining a water reservoir at a precisely controlled temperature. This reservoir feeds, through hoses, the bioreactor's outer jacket, creating a closed water circulation circuit.

The operation is relatively simple in concept, but critical in execution:

1. The bath heats or cools the water to the target temperature.
2. A circulation pump drives this water through hoses to the bioreactor jacket.
3. The water travels through the jacket, exchanging heat with the reactor's interior.
4. The water returns to the bath, where it is re-conditioned and recirculated.

The front panel of the equipment displays the current temperature and the setpoint temperature, along with buttons to activate circulation, heating, and cooling. The system is robust, but — and here lies the problem — **its panel is the only natively available reading point**.

![Ultratermostatic Bath NT 281 — display shows current temperature and setpoint](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/project/monitoramento-iot-banho-ultratermostico-bioreator/images/monitored_equipament.jpg)

---

## The Problem: A Critical Piece of Equipment with No Remote Visibility

The bioreactor, being a modern and connected device, provides temperature and other parameter data in a computer-accessible way, and it also has its own internal heating and cooling system so that the water coming from the bath enters the jacket at an appropriate temperature. The researcher can remotely track what is happening inside the reactor. However, **the ultratermostatic bath does not offer the same connectivity**.

This can create a serious operational problem. The bath is just as critical as the reactor itself. If the bath fails or goes out of its safe operating range, the consequences are severe:

- **Excessively high temperature:** can damage the bioreactor's components, or shorten the lifespan of the system, which has to work harder to bring the water into the jacket at the appropriate temperature.
- **Excessively low temperature:** can cause the circulating water to freeze, jamming the pump, interrupting the flow, and shutting down the system — immediately halting the culture.

In either scenario, the experiment can be lost. Days or weeks of cultivation, costly culture media, unique biological samples — everything can be discarded due to a failure that could have been detected and corrected in time, had there been adequate monitoring.

The researcher needs to monitor the process continuously, but the equipment is physically located in the laboratory. Checking in person every hour is not feasible, especially for long or overnight cultures. Despite the inspection and maintenance of the equipment, incidents can happen, and equipment can fail at critical hours and without supervision. Moreover, remotely monitoring all the equipment involved in costly processes makes it easier to map risks and reduce losses from operational failures, serving as one more checkpoint.

---

## The Solution: A Simple, but Transformative IoT Sensor

The researcher developed an elegant solution: she installed an **IoT temperature sensor** directly inside the ultratermostatic bath reservoir. The sensor — compact and discreet — was positioned in the stainless steel tank of the equipment, immersed in or close to the circulating water, capturing the temperature of the bath solution in real time.

![IoT sensor positioned at the back of the ultratermostatic bath, connected to the reservoir](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/project/monitoramento-iot-banho-ultratermostico-bioreator/images/IoT_positioned_next_to_the_equipment.jpg)

![Interior of the stainless steel tank with the IoT sensor installed](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/project/monitoramento-iot-banho-ultratermostico-bioreator/images/sensor_measuring_temperature_of_water.jpg)

![IoT sensor installation in the bath reservoir](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/project/monitoramento-iot-banho-ultratermostico-bioreator/images/sensor_instalation.gif)

This reading is transmitted remotely, allowing the researcher to monitor the bath temperature from her computer the same way she already monitors the bioreactor data. The solution closes a critical gap in the process monitoring ecosystem:

| Parameter | Before IoT solution | After IoT solution |
|---|---|---|
| Bioreactor temperature | ✅ Remotely monitored | ✅ Remotely monitored |
| Bath temperature | ❌ Local reading only | ✅ Remotely monitored |
| Early failure detection | ❌ Not available | ✅ Available in real time |
| Response to anomalies | ❌ Reactive (after damage) | ✅ Proactive (before damage) |

![Seu IoT platform dashboard monitoring bath temperature in real time](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/project/monitoramento-iot-banho-ultratermostico-bioreator/images/seuiot_monitoring_dashboard.png)

---

## The Value Generated: More Than Operational Convenience

At first glance, the solution may seem like a simple technological convenience — being able to see a number on screen without having to walk to the equipment. But the real value is much deeper.

**Experiment protection:** A cell culture represents investment in reagents, culture media, biological samples, and, above all, research time. An experiment lasting a week or more can be completely lost in minutes if the bath locks up due to freezing or overheating. The sensor allows detecting deviations before they become irreversible.

**Traceability and data quality:** In scientific research, documenting experimental conditions is essential for reproducibility. With the IoT sensor, bath temperature data becomes part of the process's historical record, complementing the bioreactor data.

**Operational safety:** NB2 biosafety level laboratories, like the one identified in the images, have strict operating protocols. The possibility of remote monitoring reduces the need for unnecessary entries into the laboratory, decreasing the risk of cross-contamination and researcher exposure time.

**Model scalability:** The logic applied here — instrumenting critical equipment that natively offers no connectivity with IoT sensors — is universally applicable in laboratories. Other baths, incubators, cold chambers, and analog equipment can be equally monitored with low-cost sensors, creating a layer of digital supervision that did not exist before.

---

## Conclusion

The solution developed by the researcher is a precise example of how the Internet of Things can generate real value in scientific environments — not through the complexity of the technology, but through the surgical resolution of a concrete operational pain point. With a sensor strategically positioned and integrated into the existing data flow, she transformed a critical analog device into a visible and monitorable node in her process.

The result is a safer laboratory, better-protected experiments, and a researcher with greater peace of mind — able to monitor the state of her culture from anywhere, at any time.

---
