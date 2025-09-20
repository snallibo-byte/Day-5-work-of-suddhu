import os
from PIL import Image

# Input and output folders
input_folder = "images"          # Folder where original images are kept
output_folder = "resized_images" # Folder to save resized images

# Create output folder if it doesn't exist
os.makedirs(output_folder, exist_ok=True)

# Desired size
new_size = (300, 300)   # width, height in pixels

# Loop through all files in input folder
for filename in os.listdir(input_folder):
    if filename.lower().endswith(('.png', '.jpg', '.jpeg', '.bmp', '.gif')):
        # Open image
        img_path = os.path.join(input_folder, filename)
        img = Image.open(img_path)

        # Resize image
        img_resized = img.resize(new_size)

        # Save resized image (convert JPG → PNG example)
        name, ext = os.path.splitext(filename)
        save_path = os.path.join(output_folder, f"{name}.png")
        img_resized.save(save_path)

        print(f"✅ Saved: {save_path}")

print("🎉 All images resized successfully!")
