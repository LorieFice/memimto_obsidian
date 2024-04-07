```python
import os
import matplotlib.pyplot as plt
from PIL import Image

def plot_images_in_folder(folder_path, max_columns=4):
    # Get list of image files in the folder
    image_files = [f for f in os.listdir(folder_path) if f.endswith('.jpg') or f.endswith('.png')]

    num_images = len(image_files)
    num_rows = (num_images - 1) // max_columns + 1
    
    fig, axes = plt.subplots(num_rows, max_columns, figsize=(16, 4*num_rows))
    axes = axes.flatten()
    
    for i, img_file in enumerate(image_files):
        img_path = os.path.join(folder_path, img_file)
        img = Image.open(img_path)
        axes[i].imshow(img)
        axes[i].axis('off')
        axes[i].set_title(img_file)
    
    # Hide any unused subplots
    for j in range(num_images, num_rows * max_columns):
        axes[j].axis('off')
        axes[j].set_xticks([])
        axes[j].set_yticks([])
    
    plt.tight_layout()
    plt.show()

folder_path = r'C:\Users\Thibault\Desktop\Photos imt\facile'
plot_images_in_folder(folder_path)
```
    
![png](output_0_0.png)
    

```python
import matplotlib.image as mpimg
from deepface import DeepFace
import math
from tqdm import tqdm

def get_faces(folder_path):
    faces = []
    image_files = [f for f in os.listdir(folder_path) if f.endswith('.jpg') or f.endswith('.png')]
    for i, img in enumerate(tqdm(image_files, desc="Processing images")):
        img_path = os.path.join(folder_path, img)
        img_faces = DeepFace.extract_faces(img_path, detector_backend="retinaface", enforce_detection=False)
        faces.extend(img_faces)
    print(f'{len(faces)} faces detected')
    return faces

def show_faces(folder_path):
    faces = get_faces(folder_path)
    num_faces = len(faces)
    num_rows = math.ceil(num_faces / 4)  # Calculate the number of rows needed
    plt.figure(figsize=(12, 3*num_rows))  # Adjust the figure size based on the number of rows
    for i, face_data in enumerate(faces):
        plt.subplot(num_rows, min(num_faces, 4), i+1)  # Adjust the number of columns based on the number of faces
        plt.imshow(face_data['face'])
        plt.title(f'Confidence {face_data["confidence"]}')
    plt.tight_layout()  # Automatically adjust subplot parameters to give specified padding
    plt.show()

show_faces(folder_path)
```

    Processing images: 100%|███████████████████████████████████████████████████████████████| 26/26 [02:45<00:00,  6.38s/it]
    

    76 faces detected
    


    
![png](output_1_2.png)
    

