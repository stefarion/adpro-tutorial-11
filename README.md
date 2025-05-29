# Advanced Programming - Module 11 Deployment & Monitoring
**Nama:**   &nbsp; Stefanus Tan Jaya<br>
**NPM:**    &nbsp;&ensp; 2306152456<br>
**Kelas:**  &nbsp; Pemrograman Lanjut A<br>

### Reflection 1
1. **Compare the application logs before and after you exposed it as a Service. Try to open the app several times while the proxy into the Service is running. What do you see in the logs? Does the number of logs increase each time you open the app?**<br><br>
![Bukti Log](screenshots/kubectl-logs.png)
<br><br>
Bisa dilihat perubahan pada _logs_ sebelum dan sesudah _deployment_ di-_expose_. Awalnya, _logs_ hanya menunjukkan bahwa server HTTP dapat diakses di _port_ 8080 dan server UDP dapat diakses di _port_ 8081. Kedua _logs_ awal yang dihasilkan merupakan hasil _deployment_ dan pembuatan _pods_ yang telah berhasil dijalankan. Setelah _deployment_ di-_expose_, aplikasi dapat berinteraksi dengan server di luar Kubernetes. Maka dari itu, ketika saya membuka _link service minikube_, _logs_ mencatat setiap _request_ HTTP yang masuk beserta waktunya. Tentu saja setiap kali _link service_ diakses, _logs_ akan bertambah.<br><br>

2. **Notice that there are two versions of `kubectl get` invocation during this tutorial section. The first does not have any option, while the latter has `-n` option with value set to `kube-system`. What is the purpose of the `-n` option and why did the output not list the pods/services that you explicitly created?**<br><br>
_Flag_ `-n` pada _command_ `kubectl get` berfungsi untuk mendefinisikan _namespace_ yang ingin dituju. Jika tanpa `-n`, `kubectl` akan menuju _namespace_ 'default' yang berisi _pods_ dan _service_ yang sudah di-_expose_ sebelumnya. Dengan menggunakan `-n kube-system`, `kubectl` akan menuju _namespace_ 'kube-system' yang menampilkan semua _pods_ dan _service_ yang yang diperlukan oleh sebuah _cluster_ Kubernetes untuk berjalan.