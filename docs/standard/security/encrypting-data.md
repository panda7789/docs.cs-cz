---
title: Šifrování dat
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encryption [.NET Framework], symmetric
- symmetric encryption
- cryptography [.NET Framework], asymmetric
- asymmetric encryption
ms.assetid: 7ecce51f-db5f-4bd4-9321-cceb6fcb2a77
ms.openlocfilehash: b335e0d39c1809b028e2005a472fe77729e9d267
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706211"
---
# <a name="encrypting-data"></a>Šifrování dat
Symetrické šifrování a asymetrické šifrování se provádí pomocí různých procesů. Symetrické šifrování se provádí na datových proudech a je proto užitečné pro šifrování velkých objemů dat. Asymetrické šifrování se provádí na malém počtu bajtů a je proto užitečné jenom pro malé objemy dat.  
  
## <a name="symmetric-encryption"></a>Symetrické šifrování  
 Spravované třídy symetrického kryptografie se používají se speciální třídou datového proudu s názvem <xref:System.Security.Cryptography.CryptoStream>, který šifruje data čtená do datového proudu. Třída **CryptoStream** je inicializována se třídou spravovaného datového proudu, třída implementuje rozhraní <xref:System.Security.Cryptography.ICryptoTransform> (vytvořené ze třídy, která implementuje šifrovací algoritmus), a výčet <xref:System.Security.Cryptography.CryptoStreamMode>, který popisuje typ přístupu povolený pro objekt **CryptoStream**. Třídu **CryptoStream** lze inicializovat pomocí libovolné třídy, která je odvozena od třídy <xref:System.IO.Stream>, včetně <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>a <xref:System.Net.Sockets.NetworkStream>. Pomocí těchto tříd můžete provádět symetrické šifrování u nejrůznějších objektů streamu.  
  
 Následující příklad ukazuje, jak vytvořit novou instanci třídy <xref:System.Security.Cryptography.RijndaelManaged>, která implementuje šifrovací algoritmus Rijndael a používá ho k provedení šifrování ve třídě **CryptoStream** . V tomto příkladu je **CryptoStream** inicializován s objektem datového proudu s názvem `myStream`, který může být jakýkoli typ spravovaného datového proudu. Metodě **CreateEncryptor** z třídy **RijndaelManaged** se předal klíč a IV, který se používá k šifrování. V tomto případě se použijí výchozí klíč a hodnota IV vygenerované z `rmCrypto`. Nakonec se předává **CryptoStreamMode. Write** , který zadává přístup pro zápis do datového proudu.  
  
```vb  
Dim rmCrypto As New RijndaelManaged()  
Dim cryptStream As New CryptoStream(myStream, rmCrypto.CreateEncryptor(rmCrypto.Key, rmCrypto.IV), CryptoStreamMode.Write)  
```  
  
```csharp  
RijndaelManaged rmCrypto = new RijndaelManaged();  
CryptoStream cryptStream = new CryptoStream(myStream, rmCrypto.CreateEncryptor(), CryptoStreamMode.Write);  
```  
  
 Po spuštění tohoto kódu se všechna data zapsaná do objektu **CryptoStream** šifrují pomocí algoritmu Rijndael.  
  
 Následující příklad ukazuje celý proces vytvoření datového proudu, šifrování datového proudu, zápis do datového proudu a zavření datového proudu. Tento příklad vytvoří síťový datový proud, který je zašifrovaný pomocí třídy **CryptoStream** a třídy **RijndaelManaged** . Do šifrovaného datového proudu pomocí třídy <xref:System.IO.StreamWriter> se zapisuje zpráva.  
  
> [!NOTE]
> Tento příklad můžete použít také k zápisu do souboru. Chcete-li to provést, odstraňte odkaz <xref:System.Net.Sockets.TcpClient> a nahraďte <xref:System.Net.Sockets.NetworkStream> <xref:System.IO.FileStream>.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Security.Cryptography  
Imports System.Net.Sockets  
  
Module Module1  
Sub Main()  
   Try  
      'Create a TCP connection to a listening TCP process.  
      'Use "localhost" to specify the current computer or  
      'replace "localhost" with the IP address of the   
      'listening process.   
      Dim tcp As New TcpClient("localhost", 11000)  
  
      'Create a network stream from the TCP connection.   
      Dim netStream As NetworkStream = tcp.GetStream()  
  
      'Create a new instance of the RijndaelManaged class  
      'and encrypt the stream.  
      Dim rmCrypto As New RijndaelManaged()  
  
            Dim key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
            Dim iv As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
  
      'Create a CryptoStream, pass it the NetworkStream, and encrypt   
      'it with the Rijndael class.  
      Dim cryptStream As New CryptoStream(netStream, rmCrypto.CreateEncryptor(key, iv), CryptoStreamMode.Write)  
  
      'Create a StreamWriter for easy writing to the   
      'network stream.  
      Dim sWriter As New StreamWriter(cryptStream)  
  
      'Write to the stream.  
      sWriter.WriteLine("Hello World!")  
  
      'Inform the user that the message was written  
      'to the stream.  
      Console.WriteLine("The message was sent.")  
  
      'Close all the connections.  
      sWriter.Close()  
      cryptStream.Close()  
      netStream.Close()  
      tcp.Close()  
   Catch  
      'Inform the user that an exception was raised.  
      Console.WriteLine("The connection failed.")  
   End Try  
End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Security.Cryptography;  
using System.Net.Sockets;  
  
public class main  
{  
   public static void Main(string[] args)  
   {  
      try  
      {  
         //Create a TCP connection to a listening TCP process.  
         //Use "localhost" to specify the current computer or  
         //replace "localhost" with the IP address of the   
         //listening process.    
         TcpClient tcp = new TcpClient("localhost",11000);  
  
         //Create a network stream from the TCP connection.   
         NetworkStream netStream = tcp.GetStream();  
  
         //Create a new instance of the RijndaelManaged class  
         // and encrypt the stream.  
         RijndaelManaged rmCrypto = new RijndaelManaged();  
  
         byte[] key = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
         byte[] iv = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
  
         //Create a CryptoStream, pass it the NetworkStream, and encrypt   
         //it with the Rijndael class.  
         CryptoStream cryptStream = new CryptoStream(netStream,   
         rmCrypto.CreateEncryptor(key, iv),     
         CryptoStreamMode.Write);  
  
         //Create a StreamWriter for easy writing to the   
         //network stream.  
         StreamWriter sWriter = new StreamWriter(cryptStream);  
  
         //Write to the stream.  
         sWriter.WriteLine("Hello World!");  
  
         //Inform the user that the message was written  
         //to the stream.  
         Console.WriteLine("The message was sent.");  
  
         //Close all the connections.  
         sWriter.Close();  
         cryptStream.Close();  
         netStream.Close();  
         tcp.Close();  
      }  
      catch  
      {  
         //Inform the user that an exception was raised.  
         Console.WriteLine("The connection failed.");  
      }  
   }  
}  
```  
  
 Aby byl předchozí příklad úspěšně spuštěn, musí existovat proces, který naslouchá na IP adrese a čísle portu zadané ve třídě <xref:System.Net.Sockets.TcpClient>. Pokud proces naslouchání existuje, kód se připojí k procesu naslouchání, šifruje datový proud pomocí symetrického algoritmu Rijndael a zapíše "Hello World!" do datového proudu. Pokud je kód úspěšný, zobrazí se následující text konzole:  
  
```console  
The message was sent.  
```  
  
 Nicméně pokud není nalezen žádný proces naslouchání nebo je vyvolána výjimka, kód zobrazí následující text konzole:  
  
```console  
The connection failed.  
```  
  
## <a name="asymmetric-encryption"></a>Asymetrické šifrování  
 Asymetrické algoritmy jsou obvykle používány k šifrování malých objemů dat, jako je například šifrování symetrického klíče a IV. Obvykle jednotlivec provádějící asymetrické šifrování používá veřejný klíč generovaný jinou stranou. Třídu <xref:System.Security.Cryptography.RSACryptoServiceProvider> poskytuje .NET Framework pro tento účel.  
  
 Následující příklad používá informace o veřejném klíči k šifrování symetrického klíče a IV. Jsou inicializována dvě Bajtová pole, která představují veřejný klíč třetí strany. Do těchto hodnot se inicializuje objekt <xref:System.Security.Cryptography.RSAParameters>. Dále je objekt **RSAParameters** (spolu s veřejným klíčem, který představuje) importován do parametru **RSACryptoServiceProvider** pomocí metody <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A?displayProperty=nameWithType>. Nakonec se šifrují privátní klíč a IV vytvořené třídou <xref:System.Security.Cryptography.RijndaelManaged>. V tomto příkladu je potřeba, aby systémy měly nainstalované 128 bitového šifrování.  
  
```vb  
Imports System  
Imports System.Security.Cryptography  
  
Module Module1  
  
    Sub Main()  
        'Initialize the byte arrays to the public key information.  
      Dim publicKey As Byte() =  {214, 46, 220, 83, 160, 73, 40, 39, 201, 155, 19,202, 3, 11, 191, 178, 56, 74, 90, 36, 248, 103, 18, 144, 170, 163, 145, 87, 54, 61, 34, 220, 222, 207, 137, 149, 173, 14, 92, 120, 206, 222, 158, 28, 40, 24, 30, 16, 175, 108, 128, 35, 230, 118, 40, 121, 113, 125, 216, 130, 11, 24, 90, 48, 194, 240, 105, 44, 76, 34, 57, 249, 228, 125, 80, 38, 9, 136, 29, 117, 207, 139, 168, 181, 85, 137, 126, 10, 126, 242, 120, 247, 121, 8, 100, 12, 201, 171, 38, 226, 193, 180, 190, 117, 177, 87, 143, 242, 213, 11, 44, 180, 113, 93, 106, 99, 179, 68, 175, 211, 164, 116, 64, 148, 226, 254, 172, 147}  
  
        Dim exponent As Byte() = {1, 0, 1}  
  
        'Create values to store encrypted symmetric keys.  
        Dim encryptedSymmetricKey() As Byte  
        Dim encryptedSymmetricIV() As Byte  
  
        'Create a new instance of the RSACryptoServiceProvider class.  
        Dim rsa As New RSACryptoServiceProvider()  
  
        'Create a new instance of the RSAParameters structure.  
        Dim rsaKeyInfo As New RSAParameters()  
  
        'Set rsaKeyInfo to the public key values.   
        rsaKeyInfo.Modulus = publicKey  
        rsaKeyInfo.Exponent = exponent  
  
        'Import key parameters into rsa.  
        rsa.ImportParameters(rsaKeyInfo)  
  
        'Create a new instance of the RijndaelManaged class.  
        Dim RM As New RijndaelManaged()  
  
        'Encrypt the symmetric key and IV.  
        encryptedSymmetricKey = rsa.Encrypt(RM.Key, False)  
        encryptedSymmetricIV = rsa.Encrypt(RM.IV, False)  
    End Sub  
  
End Module  
```  
  
```csharp  
using System;  
using System.Security.Cryptography;  
  
class Class1  
{  
   static void Main()  
   {  
      //Initialize the byte arrays to the public key information.  
      byte[] publicKey = {214,46,220,83,160,73,40,39,201,155,19,202,3,11,191,178,56,  
            74,90,36,248,103,18,144,170,163,145,87,54,61,34,220,222,  
            207,137,149,173,14,92,120,206,222,158,28,40,24,30,16,175,  
            108,128,35,230,118,40,121,113,125,216,130,11,24,90,48,194,  
            240,105,44,76,34,57,249,228,125,80,38,9,136,29,117,207,139,  
            168,181,85,137,126,10,126,242,120,247,121,8,100,12,201,171,  
            38,226,193,180,190,117,177,87,143,242,213,11,44,180,113,93,  
            106,99,179,68,175,211,164,116,64,148,226,254,172,147};  
  
      byte[] exponent = {1,0,1};  
  
      //Create values to store encrypted symmetric keys.  
      byte[] encryptedSymmetricKey;  
      byte[] encryptedSymmetricIV;  
  
      //Create a new instance of the RSACryptoServiceProvider class.  
      RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();  
  
      //Create a new instance of the RSAParameters structure.  
      RSAParameters rsaKeyInfo = new RSAParameters();  
  
      //Set rsaKeyInfo to the public key values.   
      rsaKeyInfo.Modulus = publicKey;  
      rsaKeyInfo.Exponent = exponent;  
  
      //Import key parameters into RSA.  
      rsa.ImportParameters(rsaKeyInfo);  
  
      //Create a new instance of the RijndaelManaged class.  
      RijndaelManaged rm = new RijndaelManaged();  
  
      //Encrypt the symmetric key and IV.  
      encryptedSymmetricKey = rsa.Encrypt(rm.Key, false);  
      encryptedSymmetricIV = rsa.Encrypt(rm.IV, false);  
   }  
}  
```  
  
## <a name="see-also"></a>Viz také:

- [Generování klíčů pro šifrování a dešifrování](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)
- [Dešifrování dat](../../../docs/standard/security/decrypting-data.md)
- [Kryptografické služby](../../../docs/standard/security/cryptographic-services.md)
