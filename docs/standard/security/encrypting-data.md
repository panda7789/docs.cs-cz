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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b583df2eb6098fa28dd8999a6796e5053d13cab4
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44135507"
---
# <a name="encrypting-data"></a>Šifrování dat
Symetrické šifrování a asymetrického šifrování se provádí pomocí jiné procesy. Symetrické šifrování se provádí na datové proudy a je proto užitečné k šifrování velkého objemu dat. Asymetrické šifrování se provádí na malý počet bajtů a proto je pouze pro malá množství dat užitečné.  
  
## <a name="symmetric-encryption"></a>Symetrické šifrování  
 Třídy spravované symetrického šifrování se používají s zvláštní datový proud třídu s názvem <xref:System.Security.Cryptography.CryptoStream> , který šifruje data načtená do datového proudu. **CryptoStream** třída je inicializována s třídou spravovaný datový proud, třída implementuje <xref:System.Security.Cryptography.ICryptoTransform> rozhraní (vytvořené z třídy, která implementuje kryptografický algoritmus) a <xref:System.Security.Cryptography.CryptoStreamMode> výčet, který Popisuje typ přístupu povolený pro **CryptoStream**. **CryptoStream** třídy mohou být inicializovány pomocí libovolné třídy, která je odvozena z <xref:System.IO.Stream> třídy, včetně <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, a <xref:System.Net.Sockets.NetworkStream>. Použití těchto tříd, můžete provést symetrické šifrování na různých objektů datového proudu.  
  
 Následující příklad ukazuje, jak vytvořit novou instanci třídy <xref:System.Security.Cryptography.RijndaelManaged> třídy, která implementuje šifrovacího algoritmu Rijndael a to pomocí provádí šifrování v **CryptoStream** třídy. V tomto příkladu **CryptoStream** je inicializován s objektem datového proudu, který volá `MyStream` , který může být libovolný typ spravovaný datový proud. **CreateEncryptor** metodu z **RijndaelManaged** třídy je předán klíč a vektor IV, který slouží k šifrování. V tomto případě výchozí klíč a vektor IV generovány z `RMCrypto` se používají. Nakonec **CryptoStreamMode.Write, který specifikuje** je předán přístup pro zápis do datového proudu.  
  
```vb  
Dim RMCrypto As New RijndaelManaged()  
Dim CryptStream As New CryptoStream(MyStream, RMCrypto.CreateEncryptor(RMCrypto.Key, RMCrypto.IV), CryptoStreamMode.Write)  
```  
  
```csharp  
RijndaelManaged RMCrypto = new RijndaelManaged();  
CryptoStream CryptStream = new CryptoStream(MyStream, RMCrypto.CreateEncryptor(), CryptoStreamMode.Write);  
```  
  
 Po spuštění tohoto kódu, všechna data zapsána do **CryptoStream** objektu je šifrovaný s použitím algoritmu Rijndael.  
  
 Následující příklad ukazuje celý proces vytváření datového proudu, šifrování datového proudu, zápis do datového proudu a zavření datového proudu. Tento příklad vytvoří datový proud sítě, který je šifrovaný s použitím **CryptoStream** třídy a **RijndaelManaged** třídy. Zapíše se do šifrovaného datového proudu s <xref:System.IO.StreamWriter> třídy.  
  
> [!NOTE]
>  V tomto příkladu můžete také použít k zápisu do souboru. K tomuto účelu odstranit <xref:System.Net.Sockets.TcpClient> odkazovat a nahraďte <xref:System.Net.Sockets.NetworkStream> s <xref:System.IO.FileStream>.  
  
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
      Dim TCP As New TcpClient("localhost", 11000)  
  
      'Create a network stream from the TCP connection.   
      Dim NetStream As NetworkStream = TCP.GetStream()  
  
      'Create a new instance of the RijndaelManaged class  
      'and encrypt the stream.  
      Dim RMCrypto As New RijndaelManaged()  
  
            Dim Key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
            Dim IV As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
  
      'Create a CryptoStream, pass it the NetworkStream, and encrypt   
      'it with the Rijndael class.  
      Dim CryptStream As New CryptoStream(NetStream, RMCrypto.CreateEncryptor(Key, IV), CryptoStreamMode.Write)  
  
      'Create a StreamWriter for easy writing to the   
      'network stream.  
      Dim SWriter As New StreamWriter(CryptStream)  
  
      'Write to the stream.  
      SWriter.WriteLine("Hello World!")  
  
      'Inform the user that the message was written  
      'to the stream.  
      Console.WriteLine("The message was sent.")  
  
      'Close all the connections.  
      SWriter.Close()  
      CryptStream.Close()  
      NetStream.Close()  
      TCP.Close()  
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
         TcpClient TCP = new TcpClient("localhost",11000);  
  
         //Create a network stream from the TCP connection.   
         NetworkStream NetStream = TCP.GetStream();  
  
         //Create a new instance of the RijndaelManaged class  
         // and encrypt the stream.  
         RijndaelManaged RMCrypto = new RijndaelManaged();  
  
         byte[] Key = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
         byte[] IV = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
  
         //Create a CryptoStream, pass it the NetworkStream, and encrypt   
         //it with the Rijndael class.  
         CryptoStream CryptStream = new CryptoStream(NetStream,   
         RMCrypto.CreateEncryptor(Key, IV),     
         CryptoStreamMode.Write);  
  
         //Create a StreamWriter for easy writing to the   
         //network stream.  
         StreamWriter SWriter = new StreamWriter(CryptStream);  
  
         //Write to the stream.  
         SWriter.WriteLine("Hello World!");  
  
         //Inform the user that the message was written  
         //to the stream.  
         Console.WriteLine("The message was sent.");  
  
         //Close all the connections.  
         SWriter.Close();  
         CryptStream.Close();  
         NetStream.Close();  
         TCP.Close();  
      }  
      catch  
      {  
         //Inform the user that an exception was raised.  
         Console.WriteLine("The connection failed.");  
      }  
   }  
}  
```  
  
 Předchozí příklad proběhl úspěšně, musí být proces, který poslouchá na IP adresu a číslo portu uvedené v <xref:System.Net.Sockets.TcpClient> třídy. Pokud naslouchací proces existuje, kód se připojit k procesu naslouchání, datového proudu pomocí algoritmu Rijndael symetrický zašifruje a zapíše "Hello World!" do datového proudu. Pokud kód je úspěšná, zobrazí následující text do konzoly:  
  
```  
The message was sent.  
```  
  
 Ale pokud je nalezen žádný naslouchací proces nebo je vyvolána výjimka, kód zobrazí následující text do konzoly:  
  
```  
The connection failed.  
```  
  
## <a name="asymmetric-encryption"></a>Asymetrické šifrování  
 Asymetrické algoritmy se obvykle používají k zašifrování malých objemů dat, třeba šifrování symetrický klíč a vektor IV. Obvykle individuální provádění asymetrického šifrování pomocí veřejného klíče generovaný jinou stranou. <xref:System.Security.Cryptography.RSACryptoServiceProvider> Třídy rozhraní .NET Framework poskytuje pro tento účel.  
  
 Následující příklad používá k šifrování symetrický klíč a vektor IV informace o veřejném klíči. Dva bajty pole jsou inicializována, které představují veřejný klíč třetích stran. <xref:System.Security.Cryptography.RSAParameters> Objekt je inicializován na tyto hodnoty. Dále **RSAParameters** objektu (spolu s veřejným klíčem, který představuje), se importují do **RSACryptoServiceProvider** pomocí <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A?displayProperty=nameWithType> metoda. Nakonec se privátní klíč a vektor IV vytvořené <xref:System.Security.Cryptography.RijndaelManaged> třídy jsou šifrovaná. Tento příklad vyžaduje systémy mají nainstalované 128bitové šifrování.  
  
```vb  
Imports System  
Imports System.Security.Cryptography  
  
Module Module1  
  
    Sub Main()  
        'Initialize the byte arrays to the public key information.  
      Dim PublicKey As Byte() =  {214, 46, 220, 83, 160, 73, 40, 39, 201, 155, 19,202, 3, 11, 191, 178, 56, 74, 90, 36, 248, 103, 18, 144, 170, 163, 145, 87, 54, 61, 34, 220, 222, 207, 137, 149, 173, 14, 92, 120, 206, 222, 158, 28, 40, 24, 30, 16, 175, 108, 128, 35, 230, 118, 40, 121, 113, 125, 216, 130, 11, 24, 90, 48, 194, 240, 105, 44, 76, 34, 57, 249, 228, 125, 80, 38, 9, 136, 29, 117, 207, 139, 168, 181, 85, 137, 126, 10, 126, 242, 120, 247, 121, 8, 100, 12, 201, 171, 38, 226, 193, 180, 190, 117, 177, 87, 143, 242, 213, 11, 44, 180, 113, 93, 106, 99, 179, 68, 175, 211, 164, 116, 64, 148, 226, 254, 172, 147}  
  
        Dim Exponent As Byte() = {1, 0, 1}  
  
        'Create values to store encrypted symmetric keys.  
        Dim EncryptedSymmetricKey() As Byte  
        Dim EncryptedSymmetricIV() As Byte  
  
        'Create a new instance of the RSACryptoServiceProvider class.  
        Dim RSA As New RSACryptoServiceProvider()  
  
        'Create a new instance of the RSAParameters structure.  
        Dim RSAKeyInfo As New RSAParameters()  
  
        'Set RSAKeyInfo to the public key values.   
        RSAKeyInfo.Modulus = PublicKey  
        RSAKeyInfo.Exponent = Exponent  
  
        'Import key parameters into RSA.  
        RSA.ImportParameters(RSAKeyInfo)  
  
        'Create a new instance of the RijndaelManaged class.  
        Dim RM As New RijndaelManaged()  
  
        'Encrypt the symmetric key and IV.  
        EncryptedSymmetricKey = RSA.Encrypt(RM.Key, False)  
        EncryptedSymmetricIV = RSA.Encrypt(RM.IV, False)  
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
      byte[] PublicKey = {214,46,220,83,160,73,40,39,201,155,19,202,3,11,191,178,56,  
            74,90,36,248,103,18,144,170,163,145,87,54,61,34,220,222,  
            207,137,149,173,14,92,120,206,222,158,28,40,24,30,16,175,  
            108,128,35,230,118,40,121,113,125,216,130,11,24,90,48,194,  
            240,105,44,76,34,57,249,228,125,80,38,9,136,29,117,207,139,  
            168,181,85,137,126,10,126,242,120,247,121,8,100,12,201,171,  
            38,226,193,180,190,117,177,87,143,242,213,11,44,180,113,93,  
            106,99,179,68,175,211,164,116,64,148,226,254,172,147};  
  
      byte[] Exponent = {1,0,1};  
  
      //Create values to store encrypted symmetric keys.  
      byte[] EncryptedSymmetricKey;  
      byte[] EncryptedSymmetricIV;  
  
      //Create a new instance of the RSACryptoServiceProvider class.  
      RSACryptoServiceProvider RSA = new RSACryptoServiceProvider();  
  
      //Create a new instance of the RSAParameters structure.  
      RSAParameters RSAKeyInfo = new RSAParameters();  
  
      //Set RSAKeyInfo to the public key values.   
      RSAKeyInfo.Modulus = PublicKey;  
      RSAKeyInfo.Exponent = Exponent;  
  
      //Import key parameters into RSA.  
      RSA.ImportParameters(RSAKeyInfo);  
  
      //Create a new instance of the RijndaelManaged class.  
      RijndaelManaged RM = new RijndaelManaged();  
  
      //Encrypt the symmetric key and IV.  
      EncryptedSymmetricKey = RSA.Encrypt(RM.Key, false);  
      EncryptedSymmetricIV = RSA.Encrypt(RM.IV, false);  
   }  
}  
```  
  
## <a name="see-also"></a>Viz také:

- [Generování klíčů pro šifrování a dešifrování](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)  
- [Dešifrování dat](../../../docs/standard/security/decrypting-data.md)  
- [Kryptografické služby](../../../docs/standard/security/cryptographic-services.md)
