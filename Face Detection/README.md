# Face Detection
## Langkah langkah Face Detection

### import cv2 dan import numpy as np:

import cv2: Baris ini mengimpor pustaka OpenCV (Open Source Computer Vision), sebuah perpustakaan yang sangat populer untuk pengolahan citra dan video. OpenCV menyediakan berbagai fungsi untuk memanipulasi gambar, seperti membaca, mengubah, dan menampilkan gambar.
import numpy as np: Mengimpor pustaka NumPy, yang sering digunakan dalam pemrograman ilmiah dan teknik untuk melakukan operasi numerik pada array. Dalam konteks pengolahan gambar, NumPy digunakan untuk merepresentasikan gambar sebagai array multidimensi.

### face_cascade = cv2.CascadeClassifier('C:/Users/LENOVO/Downloads/haarcascade_frontalface_default.xml'):

Membuat objek CascadeClassifier dari OpenCV. Objek ini digunakan untuk mendeteksi objek tertentu dalam sebuah gambar, dalam hal ini adalah wajah manusia.
File haarcascade_frontalface_default.xml adalah file yang berisi model deteksi wajah yang telah dilatih sebelumnya. Model ini telah "belajar" untuk mengenali fitur-fitur wajah yang khas, seperti mata, hidung, dan mulut.

### image = cv2.imread("C:/Users/LENOVO/Pictures/Camera Roll/WIN_20241120_09_26_08_Pro.jpg"):

Membaca gambar dari file "WIN_20241120_09_26_08_Pro.jpg" dan menyimpannya dalam variabel image.

### img = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY):

Mengubah gambar berwarna (BGR) menjadi gambar grayscale (hitam putih). Banyak algoritma pengenalan objek, termasuk deteksi wajah, bekerja lebih baik pada gambar grayscale karena mengurangi kompleksitas data.

### faces = face_cascade.detectMultiScale(img, scaleFactor=1.1):

Menggunakan metode detectMultiScale dari objek face_cascade untuk mendeteksi wajah pada gambar grayscale.
scaleFactor adalah parameter yang menentukan seberapa banyak ukuran gambar diperkecil pada setiap iterasi pencarian. Nilai yang lebih besar memungkinkan deteksi wajah yang lebih kecil, tetapi juga dapat meningkatkan jumlah deteksi palsu.

### for (x,y,w,h) in faces::

Memulai perulangan untuk setiap wajah yang ditemukan. Variabel x, y, w, dan h masing-masing mewakili koordinat x, koordinat y, lebar, dan tinggi kotak bounding yang mengelilingi wajah.

### cv2.rectangle(image, (x,y), (x+w, y+h), (0,0,155), 3):

Menggambar kotak (rectangle) pada gambar asli untuk menandai lokasi wajah yang terdeteksi.
Parameter (x,y) dan (x+w, y+h) menentukan titik sudut kiri atas dan kanan bawah kotak.
(0,0,155) adalah warna kotak dalam format BGR (biru, hijau, merah).
3 adalah ketebalan garis tepi kotak.

### cv2.imshow("display", image):

Menampilkan gambar yang telah ditandai dengan kotak-kotak di sekitar wajah dalam jendela dengan judul "display".

### cv2.waitKey(0):

Menunggu pengguna menekan tombol apa saja untuk menutup jendela tampilan.

### cv2.destroyAllWindows():

Menutup semua jendela tampilan yang sedang terbuka.
Secara singkat, kode ini melakukan:

Membaca gambar.
Mengubah gambar menjadi grayscale.
Mendeteksi wajah dalam gambar.
Menggambar kotak di sekitar wajah yang terdeteksi.
Menampilkan gambar hasil deteksi.

### Penting:

Model deteksi wajah yang digunakan dalam kode ini (haarcascade_frontalface_default.xml) dirancang khusus untuk mendeteksi wajah yang menghadap ke depan.
Kinerja deteksi dapat dipengaruhi oleh kualitas gambar, pencahayaan, ekspresi wajah, dan parameter yang digunakan dalam detectMultiScale.
Untuk deteksi wajah yang lebih kompleks dan akurat, dapat digunakan model deep learning yang lebih canggih.

## Face Detection
```python
import cv2 # menyertakan library cv2 dari opencv
import numpy as np

face_cascade = cv2.CascadeClassifier('C:/Users/LENOVO/Downloads/haarcascade_frontalface_default.xml')

image = cv2.imread("C:/Users/LENOVO/Pictures/Camera Roll/WIN_20241120_09_26_08_Pro.jpg")
img = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

faces = face_cascade.detectMultiScale(img, scaleFactor=1.1)
for (x,y,w,h) in faces: #looping sejumlah wajah yang ditemukan (xy kordinat wh lebar tinggi)
    cv2.rectangle(image, (x,y), (x+w, y+h), (0,0,155), 3)


cv2.imshow("display", image)
#cv2.imwrite("display", image)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

## Hasil
![image](https://github.com/user-attachments/assets/406bcaef-fec7-4add-8fe0-2dfc8775190c)
![image](https://github.com/user-attachments/assets/c48d6fa2-c23b-4d28-bf12-413ab3aa6abe)

