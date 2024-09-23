YOLO: prediction and output detective info
PIL: manipulating image, write texts, and drawing bounding box on frame
tkinter: providing a window GUI

code structure
before coding:
conda install pillow
conda install opencv
conda install py-cpuinfo
conda install -c conda-forge ultralytics

import : tkinter, cv2(opencv-python), ultralytics(YOLO), PIL(圖形處理套件）

PIL(Python imaging library):
support for opening, manipulating, and saving many different image file formats
  
ultralytics YOLOv8:
using yolov8n.pt - nano, smallest, fastest model, suitable for real-time applications

1.using pre-trained model - model = YOLO('yolov8n.pt') 

2.display window - class tk.frame
  open camera - cv2.VideoCapture(0)
  start and stop the video processing - self.running = False 
  create window interface - init_ui()
  display loop - 

functions
  1.release the camera or video resource to free it for other processes when you done with it. 
    __del__ - video_device.release()
  2.window interface - creating label, run button, and then pack them
    init_ui
  3.setup run button (display by start or stop status)
    set_run_button
  4.toggle run - switch the self.running status.
                  flow: 
                  init tk frame, self.running is 'False', but display 'start recognition'; 
                  when press recognition button, run 'toggle function' to invert self.running to from 'False' to 'True' by 'not' operator, display 'stop recognition'.
  5.display loop (to draw on the Tkinter window)
    a. check the status of camera device and fetch frame continuously.
    b. if boolean(succes) is True 
      1) convert the frame color to RGB format (OpenCV capture a frame as BGR format!), and it is a 'Numpy array'.
      2) create a PIL image (for Python can process it)
      3) if running recognition(self.running=True)
        A) YOLO predict this frame and save the result
        B) fetch the result 
        C) reading & drawing detective objects 
        D) display the confident & detective objects on window by Image.Draw
      4) save the drawing image
        
     
                      
