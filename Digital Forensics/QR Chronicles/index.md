# QR Chronicles

## Tools Used
- Python (for generating QR code)
- pandas (for reading Excel file)
- numpy (for matrix manipulation)
- PIL (for image generation)

The challenge provided an Excel file containing coordinates in the format row,col. The task was to interpret these coordinates as black pixels in a QR code and then generate the code to extract the flag.

The coordinates appeared to represent positions of black pixels in a QR code. I decided to use Python to:

- Extract the coordinates from the Excel file.
- Generate a binary matrix with black pixels at specified coordinates.
- Convert this matrix into a QR code image.
- Scan the QR code to retrieve the flag.

## Python Script
```
import pandas as pd
import numpy as np
from PIL import Image

# Read coordinates from Excel
def read_coordinates(file_path):
    df = pd.read_excel(file_path, header=None)
    coords = []
    for _, row in df.iterrows():
        if ':::' not in str(row[0]):
            r, c = map(int, str(row[0]).split(','))
            coords.append((r, c))
    return coords

# Generate QR code matrix from coordinates
def generate_qr(coords, size=50):
    max_row = max(c[0] for c in coords) + 1
    max_col = max(c[1] for c in coords) + 1
    qr_matrix = np.ones((max_row, max_col))
    for r, c in coords:
        qr_matrix[r, c] = 0
    return qr_matrix

# Save the QR code as an image
def save_qr(qr_matrix, output_path, scale=10):
    height, width = qr_matrix.shape
    img = Image.new('RGB', (width * scale, height * scale), 'white')
    for r in range(height):
        for c in range(width):
            if qr_matrix[r, c] == 0:
                for i in range(scale):
                    for j in range(scale):
                        img.putpixel((c * scale + i, r * scale + j), (0, 0, 0))
    img.save(output_path)

# Main execution
def main():
    coords = read_coordinates("secret_1_.xlsx")
    qr_matrix = generate_qr(coords)
    save_qr(qr_matrix, "qr_code.png")

if __name__ == "__main__":
    main()
```

After running the script, I generated a QR code, which, when scanned, revealed the flag.
`n00bz{qr_c0d3_1n_4_t3xt_f1l3_w0w!!!!!!}`

Flag - `LakshyaCTF{n00bz{qr_c0d3_1n_4_t3xt_f1l3_w0w!!!!!!}}`
