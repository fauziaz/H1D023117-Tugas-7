# Flutter - Tugas Pertemuan 7

Nama: Fauzia Azahra Depriani  
NIM: H1D023117  
Shift Lama: D  
Shift Baru: F  

---

## ⚙️ Penjelasan Kode

1. **Aplikasi dimulai dari `main.dart`**
   - Menjalankan aplikasi dengan `runApp()`
   - Menentukan routing:
     ```dart
     routes: {
       '/': (context) => const LoginPage(),
       '/home': (context) => const HomePage(),
       '/about': (context) => const AboutPage(),
     };
     ```
   - Saat pertama dibuka, aplikasi otomatis mengarah ke halaman **Login**.

---

2. **User mengisi Login di `login_page.dart`**
   - Username & password diambil menggunakan:
     ```dart
     final username = _usernameController.text;
     final password = _passwordController.text;
     ```
   - Jika login benar (`admin`):
     - Username disimpan ke **SharedPreferences**:
       ```dart
       final prefs = await SharedPreferences.getInstance();
       prefs.setString('username', username);
       ```
     - Lalu diarahkan ke Home Page:
       ```dart
       Navigator.pushReplacementNamed(context, '/home');
       ```

---

3. **HomePage membaca username dari SharedPreferences**
   - Diload saat halaman dibuka (`initState()`):
     ```dart
     final prefs = await SharedPreferences.getInstance();
     username = prefs.getString('username');
     setState(() {});
     ```
   - Jika belum terbaca → tampil loading  
   - Jika sudah terbaca → username ditampilkan pada Card:
     ```dart
     Text("Selamat datang, $username!");
     ```

---

4. **Navigasi menggunakan Drawer (`side_menu.dart`)**
   - HomePage memiliki Drawer:
     ```dart
     drawer: const SideMenu(),
     ```
   - Drawer menyediakan menu:
     - Home
     - About
     - Logout
   - Logout menghapus username dari SharedPreferences:
     ```dart
     prefs.remove('username');
     Navigator.pushReplacementNamed(context, '/');
     ```

---

5. **Halaman About (`about_page.dart`)**
   - Menampilkan informasi aplikasi:
     ```dart
     Text(
       'Aplikasi ini dibuat untuk demonstrasi Flutter Routing, '
       'Side Menu, Login System, dan Local Storage menggunakan Shared Preferences.',
     );
     ```
---

## 📸 Screenshot
1. **Login (`login_page.dart`)**
   <p align="center">
   <img src="https://github.com/user-attachments/assets/4d91c780-655f-4f98-8503-85fca71d8806" width="250" style="margin:15px;">
   <img src="https://github.com/user-attachments/assets/19c86f68-3199-4281-a863-3ef18fd74592" width="250" style="margin:15px;">
    </p>
2. **Home (`home_page.dart`)**
   <p align="center">
   <img src="https://github.com/user-attachments/assets/9a560136-3182-4d3b-82f6-e5912a7e7aa7" width="250" style="margin:15px;">
    </p>
3. **Sidemenu (`side_menu.dart`)**
   <p align="center">
   <img src="https://github.com/user-attachments/assets/01db1a8d-a427-41bd-89b4-024fdaf85b48" width="250" style="margin:15px;">
    </p>
4. **About (`about_page.dart`)**
   <p align="center">
   <img src="https://github.com/user-attachments/assets/c08a1c0e-79f7-45c9-a929-f3e5a71c9a37" width="250" style="margin:15px;">
    </p>

---

## 🎥 Demo Aplikasi
https://github.com/user-attachments/assets/7bf71adb-a54c-41de-b12e-ebea3562017b

