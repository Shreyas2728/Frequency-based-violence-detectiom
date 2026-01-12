# Frequency-based-violence-detection 
Frequency-based violence detection analyzes audio signals by extracting frequency-domain features like Mel-Frequency Cepstral Coefficients (MFCCs), spectral contrast, and Mel-spectrograms to identify patterns associated with violent sounds, such as screams or impacts. These features capture tonal and pitch variations that distinguish violence from normal audio, often processed in short windows (e.g., 10-second clips) for real-time monitoring. Upon detection, the system triggers an alert email to a specified recipient, including details like timestamp and a snapshot.

The Python script implements a simple motion-based violence detection system using OpenCV for video processing from a webcam (or CCTV feed), counting "violent" frames based on pixel change frequency over one-minute intervals, and sending email alerts via Gmail SMTP when a threshold is exceeded.

# Code Structure
The script sets a threshold_frequency of 6000 violent frames per minute—frames with over 50,000 differing pixels from the previous frame qualify as "violent" due to rapid motion indicative of potential violence. It captures video via cv2.VideoCapture(0) for the default webcam, converts frames to grayscale for efficient comparison, and uses cv2.absdiff() to compute absolute differences between consecutive frames. Non-zero pixel counts (np.count_nonzero(diff)) quantify motion; high counts trigger the counter increment.

Every 60 seconds (calculated as fps * 60 frames), it evaluates if violent_frame_count exceeds the threshold, resets the counter, and optionally displays the feed with cv2.imshow() (quit via 'q' key).

# Alert Mechanism
The send_alert() function creates an EmailMessage with a fixed "Violence detected!" body, configures it for the specified Gmail address using TLS-secured SMTP on port 587, and authenticates with a 16-character app password (required for Gmail security since 2022). Upon success, it prints "Alert sent!"; errors are caught and logged. Note: The sender and recipient are the same email, which works but limits notifications to one contact.

# Limitations and Improvements
This approach approximates "frequency-based" detection through temporal frame differencing rather than true spectral frequency analysis (e.g., no FFT via cv2.dft() for motion frequency in the Fourier domain). False positives arise from non-violent motion like wind or animals; tuning thresholds or adding Gaussian blurring before differencing reduces noise. For production, replace hardcoded credentials with environment variables, handle camera FPS dynamically, and integrate actual frequency transforms for better accuracy matching prior violence detection research. Run with python script.py after installing dependencies.
