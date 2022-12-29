/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;
import java.util.Scanner;

/**
 *
 * @author RAFI
 */
public class Koneksi {
    private Connection koneksi;
    public static void main(String[] args) {
       Connection conn = new Koneksi().Connect();
       Scanner in = new Scanner(System.in);
    }
    
    public Connection Connect() {
        
       //konsep PBO Java.Exception
       try {
           Class.forName("com.mysql.jdbc.Driver");
           System.out.println("Driver ditemukan");
       } catch (ClassNotFoundException ex) {
           System.out.println("Driver tidak ditemukan " + ex);
       }
       
       String url = "jdbc:mysql://localhost:3306/hp_cell";
       try {
           koneksi = DriverManager.getConnection(url, "root", "");
           System.out.println("Berhasil Koneksi Database");
       } catch (SQLException ex) {
           System.out.println("Gagal Koneksi Database");
       }
       return koneksi;
    }
}

