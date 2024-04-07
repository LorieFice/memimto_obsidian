Script python pour récolter des [images de l'IMT](https://photos.imt-ne.fr)

## Procédure :

- Obtenir les `ID` des images
Aller dans l'inspecteur réseau du navigateur et sauvegarder une image. 

![[Pasted image 20240404213426.png]]
https://photos.imt-ne.fr/action.php?id=73429&part=e&download=
Ici, l'`ID` est le numéro 73429
Trouver l'`ID` de la photo de fin de l'album

- Lancer le script `python`

![[Pasted image 20240404214923.png]]


Rentrer le numéro `min` et `max` des photos de l'album à télécharger, puis entrer le nom du dossier de sauvegarde

## Code

```Python
import os
import requests
from concurrent.futures import ThreadPoolExecutor
import tkinter as tk
from tkinter import ttk
import shutil

def download_image(url, filename):
    response = requests.get(url)
    if response.status_code == 200:
        with open(filename, 'wb') as f:
            f.write(response.content)
        print(f"Image téléchargée avec succès: {filename}")
        
    else:
        print(f"Échec du téléchargement de l'image: {url}")

def download_images(idmin, idmax, folder_path):
    # Create the folder if it doesn't exist
    if not os.path.exists(folder_path):
        os.makedirs(folder_path)

    # URLs of the images to download
    image_urls = ["https://photos.imt-ne.fr/action.php?id=" + str(num) + "&part=e&download=1" for num in range(idmin, idmax)]

    # Create ThreadPoolExecutor
    with ThreadPoolExecutor() as executor:
        # Download each image in parallel
        for i, url in enumerate(image_urls, start=1):
            # Create the complete path to save the image
            filepath = os.path.join(folder_path, f"image_{i}.jpg")

            # Submit download task to executor
            executor.submit(download_image, url, filepath)

    # Compress downloaded images into a zip file
    shutil.make_archive(folder_path, 'zip', folder_path)
    # Delete the original folder
    shutil.rmtree(folder_path)

def start_download():
    idmin = int(idmin_entry.get())
    idmax = int(idmax_entry.get())
    if(idmin > idmax):
        idmin, idmax = idmax, idmin
    folder_to_save = folder_path.get()
    download_images(idmin, idmax, folder_to_save)
    print('Photos téléchargées et compressées en fichier zip, le dossier original a été supprimé')

# GUI Setup
root = tk.Tk()
root.title("Téléchargement d'images")
main_frame = ttk.Frame(root, padding="20")
main_frame.grid(column=0, row=0, sticky=(tk.W, tk.E, tk.N, tk.S))
idmin_label = ttk.Label(main_frame, text="idmin:")
idmin_label.grid(column=0, row=0, sticky=tk.W)
idmin_entry = ttk.Entry(main_frame)
idmin_entry.grid(column=1, row=0)
idmax_label = ttk.Label(main_frame, text="idmax:")
idmax_label.grid(column=0, row=1, sticky=tk.W)
idmax_entry = ttk.Entry(main_frame)
idmax_entry.grid(column=1, row=1)

folder_path_label = ttk.Label(main_frame, text="Dossier de sauvegarde:")
folder_path_label.grid(column=0, row=2, sticky=tk.W)
folder_path = ttk.Entry(main_frame)
folder_path.grid(column=1, row=2)
start_button = ttk.Button(main_frame, text="Démarrer le téléchargement", command=start_download)
start_button.grid(column=0, row=3, columnspan=2, pady=10)

root.mainloop()
```
