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
ms.openlocfilehash: 39dd7bfe4e5dd3405e24bf044723dbd92ccc65a3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589825"
---
# <a name="encrypting-data"></a>Šifrování dat
Symetrické šifrování a asymetrické šifrování se provádí pomocí různých procesů. Symetrické šifrování se provádí na datové proudy, proto je užitečné k šifrování velkých objemů dat. Asymetrické šifrování se provádí na malý počet bajtů a je proto vhodné pouze pro malé množství dat.  
  
## <a name="symmetric-encryption"></a>Symetrické šifrování  
 Třídy spravované symetrického šifrování se používají s speciální datového proudu třídy s názvem <xref:System.Security.Cryptography.CryptoStream> který šifruje data načtená do datového proudu. **CryptoStream** inicializaci třídy s třídou spravovaného streamu, implementuje třídu <xref:System.Security.Cryptography.ICryptoTransform> rozhraní (vytvořen z třídy, která implementuje kryptografický algoritmus) a <xref:System.Security.Cryptography.CryptoStreamMode> výčtu, Popisuje typ oprávnění k přístupu **CryptoStream**. **CryptoStream** třída může být inicializována pomocí libovolné třídy, která je odvozena z <xref:System.IO.Stream> třídy, včetně <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, a <xref:System.Net.Sockets.NetworkStream>. Pomocí těchto tříd, můžete provést symetrického šifrování na různých objektů datového proudu.  
  
 Následující příklad ukazuje, jak vytvořit novou instanci třídy <xref:System.Security.Cryptography.RijndaelManaged> třídy, která implementuje šifrovací algoritmus Rijndael a použít ho k provedení šifrování na **CryptoStream** třídy. V tomto příkladu **CryptoStream** je inicializován s objektem datového proudu s názvem `MyStream` , mohou být jakéhokoli typu spravovaného datového proudu. **CreateEncryptor** metoda z **RijndaelManaged** třída je předán klíče a IV, které se používají pro šifrování. V takovém případě výchozí klíč a IV vygenerovaný z `RMCrypto` se používají. Nakonec **CryptoStreamMode.Write, který specifikuje** je předán přístup pro zápis do datového proudu.  
  
```vb  
Dim RMCrypto As New RijndaelManaged()  
Dim CryptStream As New CryptoStream(MyStream, RMCrypto.CreateEncryptor(RMCrypto.Key, RMCrypto.IV), CryptoStreamMode.Write)  
```  
  
```csharp  
RijndaelManaged RMCrypto = new RijndaelManaged();  
CryptoStream CryptStream = new CryptoStream(MyStream, RMCrypto.CreateEncryptor(), CryptoStreamMode.Write);  
```  
  
 Po spuštění tohoto kódu, jakákoliv data zapsána do **CryptoStream** objekt se šifruje pomocí algoritmu Rijndael.  
  
 Následující příklad ukazuje celý proces vytváření datového proudu, šifrování datového proudu, zápis do datového proudu a zavírání datového proudu. Tento příklad vytvoří datový proud sítě, který je šifrovaný pomocí **CryptoStream** třídy a **RijndaelManaged** třídy. Zpráva je zapsána do šifrovaného datového proudu pomocí <xref:System.IO.StreamWriter> třídy.  
  
> [!NOTE]
>  V tomto příkladu můžete také použít k zápisu do souboru. K tomu, odstraňte <xref:System.Net.Sockets.TcpClient> odkazovat a nahraďte <xref:System.Net.Sockets.NetworkStream> s <xref:System.IO.FileStream>.  
  
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
  
 Pro předchozí příklad proběhl úspěšně, musí být proces naslouchání na IP adresu a číslo portu zadané v <xref:System.Net.Sockets.TcpClient> třídy. Pokud naslouchací proces existuje, kód se připojit k procesu naslouchání, datového proudu pomocí algoritmu symetrického Rijndael zašifruje a zapíše "Hello, World!" do datového proudu. Pokud kód je úspěšné, zobrazí následující text do konzoly:  
  
```  
The message was sent.  
```  
  
 Ale pokud je nalezen žádný proces naslouchání nebo je vyvolána výjimka, kód zobrazí následující text do konzoly:  
  
```  
The connection failed.  
```  
  
## <a name="asymmetric-encryption"></a>Asymetrické šifrování  
 K šifrování malé množství dat, jako je například šifrování symetrického klíče a IV se obvykle používají asymetrických algoritmů. Obvykle individuální provádění asymetrického šifrování používá veřejný klíč generovaný jinou stranou. <xref:System.Security.Cryptography.RSACryptoServiceProvider> Třída poskytuje rozhraní .NET Framework pro tento účel.  
  
 Následující příklad používá k šifrování symetrického klíče a IV informace o veřejném klíči. Dva bajtová pole jsou inicializovány představující veřejný klíč třetí strany. <xref:System.Security.Cryptography.RSAParameters> Objektu je inicializována tak, aby tyto hodnoty. Dále **RSAParameters** objektu (spolu s veřejným klíčem, který reprezentuje) je importovat do **RSACryptoServiceProvider** pomocí <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A?displayProperty=nameWithType> metoda. Nakonec privátní klíč a IV vytvořené <xref:System.Security.Cryptography.RijndaelManaged> třídy jsou šifrovaná. Tento příklad vyžaduje systémy mají nainstalované 128bitové šifrování.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Generování klíčů pro šifrování a dešifrování](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)  
 [Dešifrování dat](../../../docs/standard/security/decrypting-data.md)  
 [Kryptografické služby](../../../docs/standard/security/cryptographic-services.md)
