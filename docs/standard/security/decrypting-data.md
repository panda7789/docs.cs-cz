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
ms.openlocfilehash: e287d3c73df247febf99967a9dc4b0413f01def0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353853"
---
# <a name="decrypting-data"></a>Dešifrování dat

Dešifrování je reverzní operace šifrování. U šifrování tajného klíče je nutné znát klíč i IV, které byly použity k zašifrování dat. U šifrování veřejného klíče je nutné znát buď veřejný klíč (Pokud byla data zašifrovaná pomocí privátního klíče), nebo privátní klíč (Pokud byla data zašifrovaná pomocí veřejného klíče).

## <a name="symmetric-decryption"></a>Symetrické dešifrování

Dešifrování dat šifrovaných pomocí symetrických algoritmů je podobné procesu použitému k šifrování dat pomocí symetrických algoritmů. Třída <xref:System.Security.Cryptography.CryptoStream> se používá společně se třídami symetrického kryptografie, které poskytuje .NET Framework k dešifrování dat přečtených z libovolného spravovaného objektu streamu.

Následující příklad ukazuje, jak vytvořit novou instanci třídy <xref:System.Security.Cryptography.RijndaelManaged> a použít ji k dešifrování objektu <xref:System.Security.Cryptography.CryptoStream>. Tento příklad nejprve vytvoří novou instanci třídy **RijndaelManaged** . Dále vytvoří objekt **CryptoStream** a inicializuje jej na hodnotu spravovaného datového proudu s názvem `myStream`. Dále metoda **CreateDecryptor** z třídy **RijndaelManaged** předává stejný klíč a IV, který byl použit pro šifrování a je poté předán konstruktoru **CryptoStream** . Nakonec je výčet **CryptoStreamMode. Read** předán konstruktoru **CryptoStream** , který určuje přístup pro čtení ke streamu.

```vb
Dim rmCrypto As New RijndaelManaged()
Dim cryptStream As New CryptoStream(myStream, rmCrypto.CreateDecryptor(rmCrypto.Key, rmCrypto.IV), CryptoStreamMode.Read)
```

```csharp
RijndaelManaged rmCrypto = new RijndaelManaged();
CryptoStream cryptStream = new CryptoStream(myStream, rmCrypto.CreateDecryptor(Key, IV), CryptoStreamMode.Read);
```

Následující příklad ukazuje celý proces vytvoření datového proudu, dešifrování datového proudu, čtení z datového proudu a zavření datových proudů. Vytvoří se objekt <xref:System.Net.Sockets.TcpListener>, který inicializuje síťový datový proud, když se vytvoří připojení k naslouchajícímu objektu. Síťový datový proud je poté dešifrován pomocí třídy **CryptoStream** a třídy **RijndaelManaged** . Tento příklad předpokládá, že klíč a hodnoty IV byly buď úspěšně přeneseny nebo dříve odsouhlaseny. Nezobrazuje kód potřebný k šifrování a přenos těchto hodnot.

```vb
Imports System.IO
Imports System.Net
Imports System.Net.Sockets
Imports System.Security.Cryptography
Imports System.Threading

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
using System.IO;
using System.Net;
using System.Net.Sockets;
using System.Security.Cryptography;
using System.Threading;

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
         TcpListener tcpListen = new TcpListener(IPAddress.Any, 11000);

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

Aby předchozí ukázka fungovala, musí být na naslouchací proces provedeno šifrované připojení. Připojení musí používat stejný klíč, IV a algoritmus, který se používá v naslouchací službě. Pokud je takové připojení vytvořeno, zpráva je dešifrována a zobrazena v konzole nástroje.

## <a name="asymmetric-decryption"></a>Asymetrické dešifrování

Strana (strana A) obvykle generuje veřejný i privátní klíč a ukládá klíč buď do paměti, nebo do kontejneru kryptografických klíčů. Strana A pak pošle veřejný klíč druhé straně (smluvní straně B). Když strana B použije veřejný klíč, zašifruje data a pošle je zpátky do strany A. Po přijetí dat ji strana dešifruje pomocí privátního klíče, který odpovídá. Dešifrování bude úspěšné pouze v případě, že strana A používá privátní klíč, který odpovídá veřejnému klíči B, který se používá k šifrování dat.

Informace o tom, jak uložit asymetrický klíč do kontejneru zabezpečeného kryptografického klíče a jak později získat asymetrický klíč, najdete v tématu [Postupy: ukládání asymetrických klíčů v kontejneru klíčů](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).

Následující příklad znázorňuje dešifrování dvou polí bajtů, které reprezentují symetrický klíč a IV. Informace o tom, jak extrahovat asymetrický veřejný klíč z objektu <xref:System.Security.Cryptography.RSACryptoServiceProvider> ve formátu, který lze snadno odeslat třetí straně, najdete v tématu [šifrování dat](../../../docs/standard/security/encrypting-data.md).

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
