# AI Video Coach: Instant Football Feedback


## ⚽ Project Overview

This project implements an AI-powered video analysis system for football (soccer) that provides instant feedback on passing and shooting drills. Leveraging cutting-edge computer vision techniques, the system detects the ball, tracks its movement, calculates speed, evaluates accuracy, and provides personalized improvement tips. It's designed to be a valuable tool for players and coaches looking to enhance their skills through data-driven insights.

## ✨ Features

- **Video Upload System**: Easily upload MP4 videos of your football drills.
- **AI-Powered Ball Detection**: Utilizes YOLOv8 (Ultralytics) for precise, real-time ball detection and tracking.
- **Speed Calculation**: Accurately measures ball velocity in kilometers per hour (km/h).
- **Accuracy Assessment**: Evaluates shot/pass accuracy based on a predefined target zone.
- **Visual Overlays**: Processed videos include visual annotations for ball trajectory, detection points, and target areas.
- **Performance Dashboard**: A clean, intuitive interface displaying key metrics and AI-generated coaching tips.
- **Personalized Coaching Tips**: Provides actionable feedback to help improve performance.

## 🚀 Technical Stack

- **Backend**: Django (Python Web Framework)
- **Computer Vision**: YOLOv8 (Ultralytics)
- **Video Processing**: OpenCV
- **Frontend**: Django templates (+ bootstrap)
- **Database**: SQLite (default for development)

## 📁 Project Structure

```
ai_video_coach/
├── manage.py                    # Django management script
├── requirements.txt             # Python dependencies
├── ai_video_coach/             # Main Django project settings
│   ├── settings.py             # Core Django configuration
│   ├── urls.py                 # Main URL routing
│   └── wsgi.py                 # WSGI configuration for deployment
├── coach/                      # Main application for video analysis
│   ├── models.py               # Database models (e.g., Video)
│   ├── views.py                # Request handlers and logic
│   ├── forms.py                # Django forms for video upload
│   ├── urls.py                 # Application-specific URL routing
│   ├── analyze.py              # Core video analysis logic (YOLOv8, OpenCV)
│   └── templates/              # HTML templates for the app
│       ├── base.html           # Base template for consistent UI
│       └── coach/              # App-specific templates
│           ├── upload.html     # Video upload form page
│           └── result.html     # Analysis results display page
├── media/                      # Directory for uploaded and processed videos
│   ├── videos/                 # Stores original uploaded videos
│   └── processed_videos/       # Stores analyzed videos with overlays
└── static/                     # Static files (CSS, JavaScript, images)
```

## ⚙️ Installation and Setup

Follow these steps to get the AI Video Coach up and running on your local machine:

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/ai-video-coach.git
cd ai-video-coach
```

### 2. Create a Virtual Environment (Recommended)

```bash
python3 -m venv venv
source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

If `requirements.txt` is not present, create it with the following content:

```
Django
ultralytics
opencv-python
numpy
```

### 4. Apply Database Migrations

```bash
python manage.py makemigrations
python manage.py migrate
```

### 5. Run the Development Server

```bash
python manage.py runserver
```

The application will be accessible at `http://127.0.0.1:8000/coach/upload/`.

## 🏃 Usage

1.  **Upload Video**: Navigate to the upload page (`/coach/upload/`) in your browser.
2.  **Select File**: Choose a short MP4 video of a football passing or shooting drill.
3.  **Analyze**: Click 


the "Analyze with AI" button.
4.  **View Results**: Once processed, you will be redirected to the results page showing:
    -   The processed video with visual overlays (ball detection, trajectory, target zone).
    -   Key performance metrics: ball speed and accuracy.
    -   Personalized AI coaching tips for improvement.

## 💡 How it Works

At its core, the AI Video Coach leverages the power of YOLOv8 for efficient object detection and OpenCV for robust video processing:

1.  **Video Ingestion**: Uploaded videos are read frame by frame.
2.  **Ball Detection**: For each frame, YOLOv8 identifies the football, providing its bounding box coordinates.
3.  **Trajectory Tracking**: The center point of the ball is tracked across frames to map its movement path.
4.  **Speed Calculation**: Euclidean distances between consecutive ball positions are calculated and converted to real-world meters (using an approximate pixel-to-meter factor) to estimate speed in km/h.
5.  **Accuracy Evaluation**: A predefined target zone is used to assess how accurately the ball lands, providing a percentage score.
6.  **Visual Feedback**: The original video is augmented with visual overlays (red circles for detection, blue lines for trajectory, green rectangles for target zones) to provide clear insights.
7.  **AI Coaching**: Rule-based logic generates actionable tips based on the calculated speed and accuracy.

## 📈 Future Enhancements

This project is a Minimum Viable Product (MVP) with a clear roadmap for future development:

-   **Multiple Drill Support**: Expand analysis to include dribbling, heading, and other football drills.
-   **Advanced Metrics**: Incorporate ball spin, trajectory curve analysis, and detailed technique assessment using pose estimation.
-   **User Accounts & Progress Tracking**: Allow users to create accounts, save their analysis history, and track progress over time.
-   **SaaS Platform**: Develop into a full-fledged Software as a Service (SaaS) platform with tiered subscription plans.
-   **Mobile Application**: Create native mobile apps for iOS and Android.
-   **Wearable Integration**: Connect with wearable devices for real-time data capture.

## 🤝 Contributing

Contributions are welcome! If you have suggestions for improvements or new features, please open an issue or submit a pull request. Make sure to follow the existing code style and conventions.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgements

-   [Django](https://www.djangoproject.com/)
-   [Ultralytics YOLOv8](https://ultralytics.com/yolov8)
-   [OpenCV](https://opencv.org/)
-   [Bootstrap](https://getbootstrap.com/)

---

**Built with love and passion for tech and football by Moetez Laifi - Advanced Technologies Engineering Student**


