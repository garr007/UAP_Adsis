# **LATIHAN PRAKTIKUM PENGEMBANGAN APLIKASI MOBILE**
![](Aspose.Words.c0384aa1-ccb2-4d9a-98a2-0e65fa1c9eee.001.png)BAB	: BAB 11 ANDROID SENSOR (GPS) NAMA	: Muhammad Tegar Abhiram

NIM	215150700111009

ASISTEN	: 1. BAGAS RADITYA NUR LISTYAWAN

2\. KENNETH CLINTON WAWORUNTU TANGGAL	: 2 Juni 2023

![](Aspose.Words.c0384aa1-ccb2-4d9a-98a2-0e65fa1c9eee.001.png)

# **SOAL 1**
1. ## **Soal**

Dari hasil latitude dan longitude yang didapatkan dari sensor GPS yang telah dipraktikkan sebelumnya, konversikan data tersebut menjadi sebuah alamat (nama jalan, kecamatan

,kota dll) dan tampilkan hasilnya pada layout android.

1. ## **Screenshoot**
##
## ![](Aspose.Words.c0384aa1-ccb2-4d9a-98a2-0e65fa1c9eee.002.png)
## **Gambar 1.1**
## ![](Aspose.Words.c0384aa1-ccb2-4d9a-98a2-0e65fa1c9eee.003.png)
## **Gambar 1.2**
##


1. **Penjelasan**

Untuk menampilkan Alamat yang terdiri dari nama jalan, kecamatan ,kota dll. Dapat dilakukan dengan cara menambahkan Importing Class Geocoder dan Membuat List untuk menjadi tempat menyimpan alamat tersebut.

1. Geocoder berfungsi untuk mengkonversi koordinat geografis ke dalam bentuk alamat.
1. Untuk mendapatkan koordinat geografis kita bisa menggunakan kita bisa menggunakan location.getLatitude() dan location.getLongitude() yang ada dalam class Geocoder yang nantinya dikonversi menjadi sebuah alamat
1. Jika proses konversi geocoding pada try catch berhasil dan setidaknya satu alamat ditemukan, maka alamat pertama dalam daftar alamat tersebut (addresses.get(0)) akan ditampilkan	dan	diset	ke	variable	TextView alamat.setText(addresses.get(0).getAddressLine(0)).
1. Sedangkan, getAddressLine(0) mengambil baris alamat pertama dari alamat yang ditemukan.
1. catch (IOException e) dipanggil ketika ada pengecualian saat melakukan konversi geocoding dengan memanggil e.printStackTrace();

private Geocoder geocoder;

private List<Address> addresses;

geocoder = new Geocoder(this, Locale.getDefault()); try {

addresses = geocoder.getFromLocation(location.getLatitude(), location.getLongitude(), 1);

alamat.setText(addresses.get(0).getAddressLine(0));

} catch (IOException e) {

Penambahan pada MainActivity.java

![](Aspose.Words.c0384aa1-ccb2-4d9a-98a2-0e65fa1c9eee.004.png)

e.printStackTrace();

}
![](Aspose.Words.c0384aa1-ccb2-4d9a-98a2-0e65fa1c9eee.005.png)


![](Aspose.Words.c0384aa1-ccb2-4d9a-98a2-0e65fa1c9eee.006.png)activity\_main.xml

<?xml version="1.0" encoding="utf-8"?>

<LinearLayout xmlns:android="<http://schemas.android.com/apk/res/android>" xmlns:tools="<http://schemas.android.com/tools>" tools:context=".MainActivity"

android:layout\_width="match\_parent" android:layout\_height="match\_parent" android:orientation="vertical" android:padding="14dp">

<RelativeLayout android:layout\_width="match\_parent" android:layout\_height="wrap\_content">

<TextView android:layout\_width="wrap\_content" android:layout\_height="wrap\_content" android:textColor="@color/black" android:text="Latitude" />

<TextView android:id="@+id/latitude"

android:layout\_width="wrap\_content" android:layout\_height="wrap\_content" android:textColor="@color/black" android:layout\_alignParentEnd="true" android:text="..." />

</RelativeLayout>

<RelativeLayout android:layout\_width="match\_parent" android:layout\_height="wrap\_content">

<TextView android:layout\_width="wrap\_content" android:layout\_height="wrap\_content" android:textColor="@color/black" android:text="Longitude" />

<TextView android:id="@+id/longitude" android:layout\_width="wrap\_content"

android:layout\_height="wrap\_content" android:textColor="@color/black" android:layout\_alignParentEnd="true" android:text="..." />

</RelativeLayout>

<RelativeLayout android:layout\_width="match\_parent" android:layout\_height="wrap\_content">

<TextView android:layout\_width="wrap\_content" android:layout\_height="wrap\_content" android:text="Altitude" android:textColor="@color/black" />

<TextView android:id="@+id/altitude"

android:layout\_width="wrap\_content" android:layout\_height="wrap\_content" android:textColor="@color/black" android:layout\_alignParentEnd="true" android:text="..." />

</RelativeLayout>

<RelativeLayout android:layout\_width="match\_parent" android:layout\_height="wrap\_content">

<TextView android:layout\_width="wrap\_content" android:layout\_height="wrap\_content" android:text="Akurasi" android:textColor="@color/black" />

<TextView android:id="@+id/akurasi"

android:layout\_width="wrap\_content" android:layout\_height="wrap\_content" android:textColor="@color/black" android:layout\_alignParentEnd="true" android:text="..." />

</RelativeLayout>

<RelativeLayout android:layout\_width="match\_parent" android:layout\_height="wrap\_content">

<TextView android:layout\_width="wrap\_content" android:layout\_height="wrap\_content" android:text="Alamat" android:textColor="@color/black" />

</RelativeLayout>

<RelativeLayout android:layout\_width="match\_parent" android:layout\_height="wrap\_content">

<TextView
![](Aspose.Words.c0384aa1-ccb2-4d9a-98a2-0e65fa1c9eee.007.png)

android:id="@+id/alamat" android:layout\_width="wrap\_content" android:layout\_height="wrap\_content" android:textColor="@color/black" android:layout\_alignParentEnd="true" android:text="..." />

</RelativeLayout>

<Button

android:id="@+id/btn\_find" android:layout\_width="match\_parent" android:layout\_height="wrap\_content" android:layout\_marginTop="14dp" android:textAllCaps="false" android:text="Get Location" />

</LinearLayout>
![](Aspose.Words.c0384aa1-ccb2-4d9a-98a2-0e65fa1c9eee.008.png)


![](Aspose.Words.c0384aa1-ccb2-4d9a-98a2-0e65fa1c9eee.009.png)MainActivity.java

package com.example.tugas11;

import androidx.annotation.NonNull; import android.Manifest;

import androidx.appcompat.app.AppCompatActivity; import androidx.core.app.ActivityCompat;

import android.content.pm.PackageManager; import android.location.Address;

import android.location.Geocoder; import android.os.Build;

import android.os.Bundle; import android.widget.Button; import android.widget.TextView; import android.widget.Toast;

import com.google.android.gms.location.FusedLocationProviderClient; import com.google.android.gms.location.LocationServices;

import java.io.IOException; import java.util.List;

import java.util.Locale;

public class MainActivity extends AppCompatActivity { private TextView latitude, longitude, altitude, akurasi, alamat; private Button btnFind;

private FusedLocationProviderClient locationProviderClient; private Geocoder geocoder;

private List<Address> addresses; @Override

protected void onCreate(Bundle savedInstanceState) { super.onCreate(savedInstanceState);

![](Aspose.Words.c0384aa1-ccb2-4d9a-98a2-0e65fa1c9eee.010.png)setContentView(R.layout.activity\_main); latitude = findViewById(R.id.latitude); longitude = findViewById(R.id.longitude); altitude = findViewById(R.id.altitude); akurasi = findViewById(R.id.akurasi); alamat = findViewById(R.id.alamat); btnFind = findViewById(R.id.btn\_find); locationProviderClient =

LocationServices.getFusedLocationProviderClient(MainActivity.this); geocoder = new Geocoder(this, Locale.getDefault());

btnFind.setOnClickListener(v -> { getLocation();

});

}

@Override

public void onRequestPermissionsResult(int requestCode, @NonNull String[] permissions, @NonNull int[] grantResults) {

super.onRequestPermissionsResult(requestCode, permissions, grantResults); if (requestCode == 10) {

if (ActivityCompat.checkSelfPermission(this, Manifest.permission.ACCESS\_FINE\_LOCATION) != PackageManager.PERMISSION\_GRANTED && ActivityCompat.checkSelfPermission(this, Manifest.permission.ACCESS\_COARSE\_LOCATION) != PackageManager.PERMISSION\_GRANTED) {

Toast.makeText(getApplicationContext(), "Izin lokasi tidak di aktifkan!", Toast.LENGTH\_SHORT).show();

} else {

if (Build.VERSION.SDK\_INT >= Build.VERSION\_CODES.M) {

getLocation();

}

}

}

}

private void getLocation() {

if (ActivityCompat.checkSelfPermission(this, Manifest.permission.ACCESS\_FINE\_LOCATION) != PackageManager.PERMISSION\_GRANTED && ActivityCompat.checkSelfPermission(this, Manifest.permission.ACCESS\_COARSE\_LOCATION) != PackageManager.PERMISSION\_GRANTED) {

// get Permission

if (Build.VERSION.SDK\_INT >= Build.VERSION\_CODES.M) {

requestPermissions(new String[]{Manifest.permission.ACCESS\_FINE\_LOCATION, Manifest.permission.ACCESS\_COARSE\_LOCATION}, 10);

}

} else {

// get Location

locationProviderClient.getLastLocation().addOnSuccessListener(location -> {

if (location != null) { latitude.setText(String.valueOf(location.getLatitude())); longitude.setText(String.valueOf(location.getLongitude())); altitude.setText(String.valueOf(location.getAltitude())); akurasi.setText(location.getAccuracy() + "%");

try {

addresses = geocoder.getFromLocation(location.getLatitude(), location.getLongitude(), 1);

alamat.setText(addresses.get(0).getAddressLine(0));

} catch (IOException e) { e.printStackTrace();

}

} else {

Toast.makeText(getApplicationContext(), "Lokasi tidak aktif!", Toast.LENGTH\_SHORT).show();

}

}).addOnFailureListener(e -> Toast.makeText(getApplicationContext(), e.getLocalizedMessage(), Toast.LENGTH\_SHORT).show());

}

}

}
![](Aspose.Words.c0384aa1-ccb2-4d9a-98a2-0e65fa1c9eee.011.png)


