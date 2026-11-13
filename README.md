🔬 MicroSight AI
Portable Microplastic Detection and Water Pollution Assessment System
📌 Project Overview
MicroSight AI is a portable, AI-assisted system designed for the
preliminary visual screening of suspected microplastic particles in
water samples. It combines water-sample filtration, image acquisition,
computer vision, object detection, and Big Data analytics.

The project is organized into two phases:
- Phase 1 -- Detection: Capture magnified images of filtered water
  samples and detect/count suspected particle-like objects.
- Phase 2 -- Big Data Analytics: Process detection records from
  multiple samples using Apache Spark and Scala to generate summaries
  and trends.
Important: Image-based detection indicates suspected particles
only. It does not chemically confirm that a particle is plastic.
Laboratory methods are required for material identification.

🎯 Objectives
- Capture close-up images of particles collected on membrane filters.
- Preprocess captured images using OpenCV.
- Detect and count suspected particle-like objects using a YOLOv8
  model.
- Store sample-wise detection results in CSV or JSON format.
- Clean, validate, and analyze detection records using Apache Spark
  and Scala.
- Generate source-wise, location-wise, particle-type, confidence, and
  time-based summaries.
⚙️ Technologies and Components
Hardware
- ESP32-CAM with OV2640 camera
- Compatible microscope or macro lens
- LED illumination
- Membrane filter and filter holder
- Water filtration funnel and sample containers
- Camera mount / sample platform
- Regulated power supply
- USB-to-TTL programmer for ESP32-CAM programming
Software
- Python
- OpenCV
- Ultralytics YOLOv8
- Apache Spark
- Scala
- CSV / JSON
🔄 System Workflow
Water Sample Collection
          |
          v
   Membrane Filtration
          |
          v
ESP32-CAM + Microscope Lens + LED
          |
          v
    Image Transfer
       (Wi-Fi)
          |
          v
 OpenCV Preprocessing
          |
          v
 YOLOv8 Detection
          |
          v
 Particle-like Object Count
          |
          v
   CSV / JSON Dataset
          |
          v
 Apache Spark + Scala
          |
          v
 Data Cleaning and Validation
          |
          v
 Grouping and Aggregation
          |
          v
 Analytics and Visualization
🧪 Phase 1 -- Image Acquisition and Detection
1. Collect a measured water sample and record its sample ID, source,
   location, and collection date.
2. Pass the sample through a suitable membrane filter to collect
   suspended particles.
3. Carefully prepare the filter and place it on the imaging platform.
4. Use the ESP32-CAM with a compatible close-up lens and LED
   illumination to capture the filter surface.
5. Transfer the captured image to a laptop.
6. Use OpenCV for suitable image preprocessing.
7. Run the YOLOv8 model to detect trained particle classes and produce
   bounding boxes and confidence scores.
8. Save the detection information for each sample.
Example Detection Record
  Sample_ID   Source    Location   Particle_Type     Particle_Count   Average_Confidence Collection_Date
  S001        River     Chennai    Fragment                      24                 0.91 2026-01-05
S002        River     Chennai    Fiber                         31                 0.88 2026-01-10
The values above are illustrative sample data, not measured
experimental results.
📊 Phase 2 -- Apache Spark and Scala Analytics
Phase 2 analyzes structured detection records generated in Phase 1.
YOLOv8 performs image-level detection; Spark and Scala process the
resulting tabular data.
Processing Steps
1. Export Phase 1 results to CSV or JSON.
2. Create a SparkSession using Scala.
3. Load the dataset into a Spark DataFrame.
4. Validate schema, data types, missing values, duplicates, and invalid
   records.
5. Standardize source, location, and date fields where required.
6. Apply DataFrame transformations and actions.
7. Generate analytical summaries and export the results.
Planned Analytics
- Total and Average Particle Count: Summarize particle counts
  across samples.
- Source-wise Analysis: Compare River, Lake, Pond, and Tap Water
  records.
- Location-wise Analysis: Compare results by sampling location.
- Particle-type Analysis: Summarize detected categories such as
  Fiber and Fragment.
- Confidence Analysis: Calculate average, minimum, and maximum
  model confidence.
- Time-based Analysis: Examine date-wise and month-wise count
  patterns.
- Preliminary Screening Categories: Compare samples using clearly
  defined project thresholds, if validated.
📁 Suggested Repository Structure
MicroSight-AI/
│
├── README.md
├── hardware/
│   ├── component-list.md
│   ├── wiring-diagram/
│   └── esp32_cam/
│
├── phase1_detection/
│   ├── image_capture/
│   ├── opencv/
│   ├── yolov8/
│   └── detection_output/
│
├── phase2_analytics/
│   ├── scala/
│   ├── spark/
│   └── output/
│
├── dataset/
│   └── sample_dataset.csv
│
├── docs/
│   ├── system-architecture/
│   └── project-images/
│
└── requirements.txt
This is a suggested structure. Update it to match the files actually
included in the repository.
📈 Expected Outputs
- Original image captured from the membrane filter
- Processed image with detection bounding boxes and labels
- Particle-like object count and confidence scores
- Sample-wise CSV/JSON detection dataset
- Source-wise and location-wise summaries
- Particle-type distribution
- Confidence-score statistics
- Date-wise and month-wise trends
- Exported analytical reports and visualizations
🛠️ Setup and Execution
Hardware Setup
1. Assemble the filtration unit and imaging platform.
2. Mount the ESP32-CAM and compatible lens.
3. Install and position the LED illumination.
4. Program the ESP32-CAM and verify image capture.
5. Confirm that images can be transferred to the laptop over Wi-Fi.
Phase 1 Software
1. Set up the Python environment.
2. Install the dependencies used by the project.
3. Configure the ESP32-CAM image source.
4. Configure the trained YOLOv8 model and its class labels.
5. Run image preprocessing and detection.
6. Export sample-wise detection results.
Phase 2 Software
1. Install and configure compatible Java, Scala, and Apache Spark
   versions.
2. Configure the input CSV/JSON dataset path.
3. Run the Scala Spark application.
4. Check the generated analytical outputs.
Exact commands, dependency versions, model weights, and configuration
values should be added after confirming the actual implementation in
the repository.

⚠️ Limitations
- Detection performance depends on image quality, lighting, lens
  magnification, and the training dataset.
- The YOLOv8 model can only detect classes it has been trained and
  validated to recognize.
- Visual appearance alone cannot establish the chemical composition of
  a particle.
- Contamination categories such as Low, Medium, and High require
  defined and validated thresholds.
- Reliable performance claims require comparison with manually
  verified results and, where possible, laboratory validation.
🚀 Future Enhancements
- Improve the training dataset with diverse, carefully labeled
  particle images.
- Improve camera focus, illumination, and imaging consistency.
- Add more water sources and sampling locations.
- Develop an interactive analytics dashboard.
- Automate batch processing and report generation.
- Validate image-based screening results against laboratory
  identification methods.
🌍 Project Impact
MicroSight AI aims to provide an accessible prototype for preliminary
visual screening and structured analysis of suspected particles in water
samples. By combining portable image acquisition, computer vision, and
scalable data analytics, the project offers a foundation for further
environmental monitoring research.
👥 Contributors
Add the names and roles of the project team members here.
📚 References
- Ultralytics YOLO Documentation
- OpenCV Documentation
- Apache Spark Documentation
- Scala Documentation
Project: MicroSight AI
Domain: Artificial Intelligence, Computer Vision, Big Data
Analytics, Environmental Monitoring
