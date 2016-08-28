
Se deben importar las siguientes librerias:

import java.io.BufferedWriter;
import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.FileWriter;
import java.io.IOException;
import javax.xml.bind.DatatypeConverter;

    public static void main(String[] args) throws IOException{
        
        File imgA = new File("C:/fotos_rtm/A.jpg");
        File imgB = new File("C:/fotos_rtm/B.jpg");
        
        String Base64ImgA = ImgToBase64(imgA);
        String Base64ImgB = ImgToBase64(imgB);

        String cadena = Base64ImgA + ";" + Base64ImgB;
        
        CrearTXT(cadena);
        
    }
    
 Metodo para convertir img a Base64
     
    
    public static String ImgToBase64(File img){
        
        String encodedBase64 = null;
        
        try {
            
            FileInputStream fileInputStreamReader = new FileInputStream(img);
            byte[] bytes = new byte[(int)img.length()];
            fileInputStreamReader.read(bytes);
            encodedBase64 = new String( DatatypeConverter.printBase64Binary(bytes) );
          
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        }
        
        return encodedBase64;
    }
 
 Metodo para crear archivo TXT apartir de una cadena recibida
    
    public static void CrearTXT(String cadena) throws IOException{
        String ruta = "C:/fotos_rtm/c.txt";
        File archivo = new File(ruta);
        BufferedWriter bw;
        if(archivo.exists()) {
            bw = new BufferedWriter(new FileWriter(archivo));
            bw.write(cadena);
        } else {
            bw = new BufferedWriter(new FileWriter(archivo));
            bw.write(cadena);
        }
        bw.close();
    }
    
}
