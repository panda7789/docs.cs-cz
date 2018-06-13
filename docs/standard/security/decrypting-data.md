---
title: Dešifrování dat
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [.NET Framework], decryption
- symmetric decryption
- asymmetric decryption
- decryption
ms.assetid: 9b266b6c-a9b2-4d20-afd8-b3a0d8fd48a0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d0aefcc61a9ce283f1230cd44ffae549725bb15f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589094"
---
# <a name="decrypting-data"></a>Dešifrování dat
Dešifrování je reverzní operace šifrování. K šifrování tajného klíče musíte znát IV, které jste použili k šifrování dat i klíč. K šifrování veřejného klíče musíte znát veřejný klíč (Pokud byla data zašifrována pomocí soukromého klíče) nebo privátní klíč (Pokud byla data zašifrována pomocí veřejného klíče).  
  
## <a name="symmetric-decryption"></a>Symetrické dešifrování  
 Dešifrování dat šifrován symetrické algoritmy je podobný proces používaný k šifrování dat symetrickými algoritmy. <xref:System.Security.Cryptography.CryptoStream> Třída se používá se symetrické šifrování třídy poskytované rozhraní .NET Framework dešifrovat data načíst z libovolného objektu spravovaného streamu.  
  
 Následující příklad ukazuje, jak vytvořit novou instanci třídy <xref:System.Security.Cryptography.RijndaelManaged> třídy a použít ho k dešifrování na <xref:System.Security.Cryptography.CryptoStream> objektu. Tento příklad nejprve vytvoří novou instanci třídy **RijndaelManaged** třídy. Potom vytvoří **CryptoStream** objekt a inicializuje ji na hodnotu spravovaného streamu volat `MyStream`. Dále **CreateDecryptor** metoda z **RijndaelManaged** třída je předán stejný klíč a IV, který byl použit pro šifrování a pak je předána **CryptoStream** konstruktor. Nakonec **CryptoStream** výčtu je předán **CryptoStream** konstruktor k zadání přístupu pro čtení do datového proudu.  
  
```vb  
Dim RMCrypto As New RijndaelManaged()  
Dim CryptStream As New CryptoStream(MyStream, RMCrypto.CreateDecryptor(RMCrypto.Key, RMCrypto.IV), CryptoStreamMode.Read)  
```  
  
```csharp  
RijndaelManaged RMCrypto = new RijndaelManaged();  
CryptoStream CryptStream = new CryptoStream(MyStream, RMCrypto.CreateDecryptor(Key, IV), CryptoStreamMode.Read);  
```  
  
 Následující příklad ukazuje celý proces vytváření datového proudu, dešifrování datového proudu, čtení z datového proudu a zavření datových proudů. A <xref:System.Net.Sockets.TcpListener> je vytvořen objekt, který inicializuje datový proud sítě při připojení k objektu naslouchání. Datový proud sítě je pak dešifrovat pomocí **CryptoStream** – třída a **RijndaelManaged** třídy. Tento příklad předpokládá, že klíče a hodnoty IV byly buď úspěšně přenesla nebo dříve schválené. Kód potřebný k šifrování a přenos tyto hodnoty nejsou zobrazeny.  
  
```vb  
Imports System  
Imports System.Net.Sockets  
Imports System.Threading  
Imports System.IO  
Imports System.Net  
Imports System.Security.Cryptography  
  
Module Module1  
    Sub Main()  
            'The key and IV must be the same values that were used  
            'to encrypt the stream.    
            Dim Key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
            Dim IV As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
        Try  
            'Initialize a TCPListener on port 11000  
            'using the current IP address.  
            Dim TCPListen As New TcpListener(IPAddress.Any, 11000)  
  
            'Start the listener.  
            TCPListen.Start()  
  
            'Check for a connection every five seconds.  
            While Not TCPListen.Pending()  
                Console.WriteLine("Still listening. Will try in 5 seconds.")  
  
                Thread.Sleep(5000)  
            End While  
  
            'Accept the client if one is found.  
            Dim TCP As TcpClient = TCPListen.AcceptTcpClient()  
  
            'Create a network stream from the connection.  
            Dim NetStream As NetworkStream = TCP.GetStream()  
  
            'Create a new instance of the RijndaelManaged class  
            'and decrypt the stream.  
            Dim RMCrypto As New RijndaelManaged()  
  
            'Create an instance of the CryptoStream class, pass it the NetworkStream, and decrypt   
            'it with the Rijndael class using the key and IV.  
            Dim CryptStream As New CryptoStream(NetStream, RMCrypto.CreateDecryptor(Key, IV), CryptoStreamMode.Read)  
  
            'Read the stream.  
            Dim SReader As New StreamReader(CryptStream)  
  
            'Display the message.  
            Console.WriteLine("The decrypted original message: {0}", SReader.ReadToEnd())  
  
            'Close the streams.  
            SReader.Close()  
            NetStream.Close()  
            TCP.Close()  
            'Catch any exceptions.   
        Catch  
            Console.WriteLine("The Listener Failed.")  
        End Try  
    End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Net.Sockets;  
using System.Threading;  
using System.IO;  
using System.Net;  
using System.Security.Cryptography;  
  
class Class1  
{  
   static void Main(string[] args)  
   {  
      //The key and IV must be the same values that were used  
      //to encrypt the stream.    
      byte[] Key = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
      byte[] IV = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
      try  
      {  
         //Initialize a TCPListener on port 11000  
         //using the current IP address.  
         TcpListener TCPListen = new TcpListener(IPAdress.Any, 11000);  
  
         //Start the listener.  
         TCPListen.Start();  
  
         //Check for a connection every five seconds.  
         while(!TCPListen.Pending())  
         {  
            Console.WriteLine("Still listening. Will try in 5 seconds.");  
            Thread.Sleep(5000);  
         }  
  
         //Accept the client if one is found.  
         TcpClient TCP = TCPListen.AcceptTcpClient();  
  
         //Create a network stream from the connection.  
         NetworkStream NetStream = TCP.GetStream();  
  
         //Create a new instance of the RijndaelManaged class  
         // and decrypt the stream.  
         RijndaelManaged RMCrypto = new RijndaelManaged();  
  
         //Create a CryptoStream, pass it the NetworkStream, and decrypt   
         //it with the Rijndael class using the key and IV.  
         CryptoStream CryptStream = new CryptoStream(NetStream,   
            RMCrypto.CreateDecryptor(Key, IV),   
            CryptoStreamMode.Read);  
  
         //Read the stream.  
         StreamReader SReader = new StreamReader(CryptStream);  
  
         //Display the message.  
         Console.WriteLine("The decrypted original message: {0}", SReader.ReadToEnd());  
  
         //Close the streams.  
         SReader.Close();  
         NetStream.Close();  
         TCP.Close();  
      }  
      //Catch any exceptions.   
      catch  
      {  
         Console.WriteLine("The Listener Failed.");  
      }  
   }  
}  
```  
  
 Předchozí příklad, fungovat šifrované připojení musí být provedeny pro naslouchací proces. Připojení k musí používat stejný klíč, IV a algoritmus používaný v naslouchací proces. Pokud se toto připojení, je zpráva dešifrovat a zobrazení v konzole.  
  
## <a name="asymmetric-decryption"></a>Asymetrické dešifrování  
 Obvykle strany (strany A) generuje jak veřejný a privátní klíč a ukládá klíče v paměti nebo v kontejneru kryptografických klíčů.  Strany, A poté odešle veřejný klíč na druhé straně (straně B).  Pomocí veřejného klíče, strany B šifruje data a odešle data straně a.  Po přijetí dat, strany A dešifruje ji pomocí privátního klíče, který odpovídá.  Dešifrování bude úspěšné pouze v případě, že používá privátního klíče, který odpovídá veřejnému klíči strany B používá k šifrování dat A strany.  
  
 Informace o tom, jak ukládat asymetrického klíče v zabezpečeném kontejneru kryptografických klíčů a jak později načíst asymetrický klíč, najdete v části [postupy: ukládání asymetrických klíčů v kontejneru klíčů](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).  
  
 Následující příklad ilustruje dešifrování dvě pole bajtů, které představují symetrický klíč a IV.  Informace o tom, jak extrahovat asymetrické veřejného klíče z <xref:System.Security.Cryptography.RSACryptoServiceProvider> objekt ve formátu, který lze snadno odeslat třetích stran, najdete v článku [šifrování dat](../../../docs/standard/security/encrypting-data.md).  
  
```vb  
'Create a new instance of the RSACryptoServiceProvider class.  
Dim RSA As New RSACryptoServiceProvider()  
  
' Export the public key information and send it to a third party.  
' Wait for the third party to encrypt some data and send it back.  
  
'Decrypt the symmetric key and IV.  
SymmetricKey = RSA.Decrypt(EncryptedSymmetricKey, False)  
SymmetricIV = RSA.Decrypt(EncryptedSymmetricIV, False)  
```  
  
```csharp  
//Create a new instance of the RSACryptoServiceProvider class.  
RSACryptoServiceProvider RSA = new RSACryptoServiceProvider();  
  
// Export the public key information and send it to a third party.  
// Wait for the third party to encrypt some data and send it back.  
  
//Decrypt the symmetric key and IV.  
SymmetricKey = RSA.Decrypt( EncryptedSymmetricKey, false);  
SymmetricIV = RSA.Decrypt( EncryptedSymmetricIV , false);  
```  
  
## <a name="see-also"></a>Viz také  
 [Generování klíčů pro šifrování a dešifrování](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)  
 [Šifrování dat](../../../docs/standard/security/encrypting-data.md)  
 [Kryptografické služby](../../../docs/standard/security/cryptographic-services.md)
