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
ms.openlocfilehash: 3cb0b010a7b5f3e9baaf1c075bfbcf25cea842fe
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2019
ms.locfileid: "56583482"
---
# <a name="decrypting-data"></a>Dešifrování dat
Dešifrování se zpětná operace šifrování. K šifrování tajného klíče musíte znát klíč a vektor IV použitý k šifrování dat. Pro šifrování s veřejným klíčem je třeba znát veřejného klíče (Pokud byla data zašifrována pomocí soukromého klíče) nebo privátní klíč (Pokud byla data zašifrována pomocí veřejného klíče).  
  
## <a name="symmetric-decryption"></a>Symetrické dešifrování  
 Dešifrování data zašifrovaná pomocí symetrických algoritmů je podobný procesu použité k šifrování dat pomocí symetrických algoritmů. <xref:System.Security.Cryptography.CryptoStream> Třída se používá s třídami symetrické šifrování poskytované rozhraní .NET Framework se dešifrovat data načtená z libovolného objektu spravovaný datový proud.  
  
 Následující příklad ukazuje, jak vytvořit novou instanci třídy <xref:System.Security.Cryptography.RijndaelManaged> třídy a použít ho k dešifrování na <xref:System.Security.Cryptography.CryptoStream> objektu. Tento příklad nejprve vytvoří novou instanci třídy **RijndaelManaged** třídy. Vedle vytváření **CryptoStream** objektu a inicializuje ji na hodnotu spravovaný datový proud volá `myStream`. Dále **CreateDecryptor** metodu z **RijndaelManaged** třídy je předán stejný klíč a vektor IV, který se použil pro šifrování a je pak předán **CryptoStream** konstruktor. Nakonec **CryptoStream** výčtu je předán **CryptoStream** konstruktor k zadání oprávnění ke čtení pro datový proud.  
  
```vb  
Dim rmCrypto As New RijndaelManaged()  
Dim cryptStream As New CryptoStream(myStream, rmCrypto.CreateDecryptor(rmCrypto.Key, rmCrypto.IV), CryptoStreamMode.Read)  
```  
  
```csharp  
RijndaelManaged rmCrypto = new RijndaelManaged();  
CryptoStream cryptStream = new CryptoStream(myStream, rmCrypto.CreateDecryptor(Key, IV), CryptoStreamMode.Read);  
```  
  
 Následující příklad ukazuje celý proces vytváření datového proudu, dešifrování datového proudu, čtení z datového proudu a zavření datových proudů. A <xref:System.Net.Sockets.TcpListener> je vytvořen objekt, který inicializuje sítě datového proudu při připojení k naslouchání objektu. Datový proud sítě je pak dešifrovat pomocí **CryptoStream** třídy a **RijndaelManaged** třídy. Tento příklad předpokládá, že klíč a vektor IV hodnoty byly buď úspěšně převeden nebo dříve dohodnutých. Nezobrazuje se kód potřebný k šifrování a přenést tyto hodnoty.  
  
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
            Dim key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
            Dim iv As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
        Try  
            'Initialize a TCPListener on port 11000  
            'using the current IP address.  
            Dim tcpListen As New TcpListener(IPAddress.Any, 11000)  
  
            'Start the listener.  
            tcpListen.Start()  
  
            'Check for a connection every five seconds.  
            While Not tcpListen.Pending()  
                Console.WriteLine("Still listening. Will try in 5 seconds.")  
  
                Thread.Sleep(5000)  
            End While  
  
            'Accept the client if one is found.  
            Dim tcp As TcpClient = tcpListen.AcceptTcpClient()  
  
            'Create a network stream from the connection.  
            Dim netStream As NetworkStream = tcp.GetStream()  
  
            'Create a new instance of the RijndaelManaged class  
            'and decrypt the stream.  
            Dim rmCrypto As New RijndaelManaged()  
  
            'Create an instance of the CryptoStream class, pass it the NetworkStream, and decrypt   
            'it with the Rijndael class using the key and IV.  
            Dim cryptStream As New CryptoStream(netStream, rmCrypto.CreateDecryptor(key, iv), CryptoStreamMode.Read)  
  
            'Read the stream.  
            Dim sReader As New StreamReader(cryptStream)  
  
            'Display the message.  
            Console.WriteLine("The decrypted original message: {0}", sReader.ReadToEnd())  
  
            'Close the streams.  
            sReader.Close()  
            netStream.Close()  
            tcp.Close()  
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
      byte[] key = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
      byte[] iv = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
      try  
      {  
         //Initialize a TCPListener on port 11000  
         //using the current IP address.  
         TcpListener tcpListen = new TcpListener(IPAdress.Any, 11000);  
  
         //Start the listener.  
         tcpListen.Start();  
  
         //Check for a connection every five seconds.  
         while(!tcpListen.Pending())  
         {  
            Console.WriteLine("Still listening. Will try in 5 seconds.");  
            Thread.Sleep(5000);  
         }  
  
         //Accept the client if one is found.  
         TcpClient tcp = tcpListen.AcceptTcpClient();  
  
         //Create a network stream from the connection.  
         NetworkStream netStream = tcp.GetStream();  
  
         //Create a new instance of the RijndaelManaged class  
         // and decrypt the stream.  
         RijndaelManaged rmCrypto = new RijndaelManaged();  
  
         //Create a CryptoStream, pass it the NetworkStream, and decrypt   
         //it with the Rijndael class using the key and IV.  
         CryptoStream cryptStream = new CryptoStream(netStream,   
            rmCrypto.CreateDecryptor(key, iv),   
            CryptoStreamMode.Read);  
  
         //Read the stream.  
         StreamReader sReader = new StreamReader(cryptStream);  
  
         //Display the message.  
         Console.WriteLine("The decrypted original message: {0}", sReader.ReadToEnd());  
  
         //Close the streams.  
         sReader.Close();  
         netStream.Close();  
         tcp.Close();  
      }  
      //Catch any exceptions.   
      catch  
      {  
         Console.WriteLine("The Listener Failed.");  
      }  
   }  
}  
```  
  
 Předchozí ukázka fungovala musí provést šifrované připojení k naslouchacímu procesu. Připojení musí používat stejný klíč, IV a algoritmus používaný v naslouchací proces. Pokud je toto připojení, zpráva se dešifrují a zobrazí v konzole.  
  
## <a name="asymmetric-decryption"></a>Asymetrické dešifrování  
 Strana (stran A) obvykle generuje i veřejného a privátního klíče a uloží klíč v paměti nebo v kontejneru kryptografických klíčů.  Party, A poté odešle veřejný klíč do jiného (strana B).  Pomocí veřejného klíče, strana B šifruje data a odešle data zpět do strany A.  Po přijetí dat, strana A dešifruje ji pomocí soukromého klíče, který odpovídá.  Dešifrování bude úspěšné pouze v případě, že strana A privátní klíč, který odpovídá veřejnému klíči stran B používá k šifrování dat používá.  
  
 Informace o způsobu uložení asymetrického klíče v kontejneru zabezpečené kryptografické klíče a jak později načíst asymetrického klíče, naleznete v tématu [jak: Store asymetrického klíče v kontejneru klíčů](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).  
  
 Následující příklad ukazuje dešifrování dvě pole bajtů, která představuje symetrický klíč a vektor IV.  Informace o tom, jak extrahovat asymetrického veřejný klíč z <xref:System.Security.Cryptography.RSACryptoServiceProvider> objektu ve formátu, který můžete snadno odesílat žádné třetí straně, přečtěte si téma [šifrování dat](../../../docs/standard/security/encrypting-data.md).  
  
```vb  
'Create a new instance of the RSACryptoServiceProvider class.  
Dim rsa As New RSACryptoServiceProvider()  
  
' Export the public key information and send it to a third party.  
' Wait for the third party to encrypt some data and send it back.  

'Decrypt the symmetric key and IV.  
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, False)  
symmetricIV = rsa.Decrypt(encryptedSymmetricIV, False)  
```  
  
```csharp  
//Create a new instance of the RSACryptoServiceProvider class.  
RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();  
  
// Export the public key information and send it to a third party.  
// Wait for the third party to encrypt some data and send it back.  

//Decrypt the symmetric key and IV.  
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, false);  
symmetricIV = rsa.Decrypt(encryptedSymmetricIV , false);  
```  
  
## <a name="see-also"></a>Viz také:

- [Generování klíčů pro šifrování a dešifrování](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)
- [Šifrování dat](../../../docs/standard/security/encrypting-data.md)
- [Kryptografické služby](../../../docs/standard/security/cryptographic-services.md)
