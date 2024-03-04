# Cara menjalankan aplikasi web deteksi helm dari perlengkapan APD
```
$ cd web_apd_detector
$ python -m http.server
Buka 'localhost:8000' di browser
```

**Tolong jangan menggunakan http://0.0.0.0:8000/ agar model tensorflowjs tidak terblokir.**

<span style="color:red;">This text is red.</span>
# Proses pencarian dataset
Saya memilih dataset object detection helm dari url berikut
https://universe.roboflow.com/hardhats/hardhats-ctl1u/dataset/2/images
Saya memilih dataset ini karena sudah diberikan bounding box di sekitar gambar helm yang digunakan seseorang. Data juga sudah diberikan label 'helmet' sebagai label menggunakan helm dan 'head' sebagai label tidak menggunakan helm. Dibandingkan dengan data lain yang saya lihat, data ini juga sudah terlihat bersih dan tidak ada label atau box yang tidak berhubungan dengan objek deteksi helm.

# Preprocessing
Preprocessing dilakukan secara lokal untuk menghemat unit compute google collab.

1. Data diunduh dengan format CSV Tensorflow Object Detection.
2. Konversi dataset gambar ke tfrecord
3. Compress dataset tfrecord ke .tar.xz
4. Karena proses training dilakukan melalui google collab, Dataset diupload ke dropbox agar proses download di google collab menjadi cepat.

# Training
Proses latih model AI dilakukan di **training_object_detection.ipynb**