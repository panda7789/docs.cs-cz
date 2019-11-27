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
# <a name="decrypting-data"></a><span data-ttu-id="6f9c9-102">Dešifrování dat</span><span class="sxs-lookup"><span data-stu-id="6f9c9-102">Decrypting Data</span></span>

<span data-ttu-id="6f9c9-103">Dešifrování je reverzní operace šifrování.</span><span class="sxs-lookup"><span data-stu-id="6f9c9-103">Decryption is the reverse operation of encryption.</span></span> <span data-ttu-id="6f9c9-104">U šifrování tajného klíče je nutné znát klíč i IV, které byly použity k zašifrování dat.</span><span class="sxs-lookup"><span data-stu-id="6f9c9-104">For secret-key encryption, you must know both the key and IV that were used to encrypt the data.</span></span> <span data-ttu-id="6f9c9-105">U šifrování veřejného klíče je nutné znát buď veřejný klíč (Pokud byla data zašifrovaná pomocí privátního klíče), nebo privátní klíč (Pokud byla data zašifrovaná pomocí veřejného klíče).</span><span class="sxs-lookup"><span data-stu-id="6f9c9-105">For public-key encryption, you must know either the public key (if the data was encrypted using the private key) or the private key (if the data was encrypted using the public key).</span></span>

## <a name="symmetric-decryption"></a><span data-ttu-id="6f9c9-106">Symetrické dešifrování</span><span class="sxs-lookup"><span data-stu-id="6f9c9-106">Symmetric Decryption</span></span>

<span data-ttu-id="6f9c9-107">Dešifrování dat šifrovaných pomocí symetrických algoritmů je podobné procesu použitému k šifrování dat pomocí symetrických algoritmů.</span><span class="sxs-lookup"><span data-stu-id="6f9c9-107">The decryption of data encrypted with symmetric algorithms is similar to the process used to encrypt data with symmetric algorithms.</span></span> <span data-ttu-id="6f9c9-108">Třída <xref:System.Security.Cryptography.CryptoStream> se používá společně se třídami symetrického kryptografie, které poskytuje .NET Framework k dešifrování dat přečtených z libovolného spravovaného objektu streamu.</span><span class="sxs-lookup"><span data-stu-id="6f9c9-108">The <xref:System.Security.Cryptography.CryptoStream> class is used with symmetric cryptography classes provided by the .NET Framework to decrypt data read from any managed stream object.</span></span>

<span data-ttu-id="6f9c9-109">Následující příklad ukazuje, jak vytvořit novou instanci třídy <xref:System.Security.Cryptography.RijndaelManaged> a použít ji k dešifrování objektu <xref:System.Security.Cryptography.CryptoStream>.</span><span class="sxs-lookup"><span data-stu-id="6f9c9-109">The following example illustrates how to create a new instance of the <xref:System.Security.Cryptography.RijndaelManaged> class and use it to perform decryption on a <xref:System.Security.Cryptography.CryptoStream> object.</span></span> <span data-ttu-id="6f9c9-110">Tento příklad nejprve vytvoří novou instanci třídy **RijndaelManaged** .</span><span class="sxs-lookup"><span data-stu-id="6f9c9-110">This example first creates a new instance of the **RijndaelManaged** class.</span></span> <span data-ttu-id="6f9c9-111">Dále vytvoří objekt **CryptoStream** a inicializuje jej na hodnotu spravovaného datového proudu s názvem `myStream`.</span><span class="sxs-lookup"><span data-stu-id="6f9c9-111">Next it creates a **CryptoStream** object and initializes it to the value of a managed stream called `myStream`.</span></span> <span data-ttu-id="6f9c9-112">Dále metoda **CreateDecryptor** z třídy **RijndaelManaged** předává stejný klíč a IV, který byl použit pro šifrování a je poté předán konstruktoru **CryptoStream** .</span><span class="sxs-lookup"><span data-stu-id="6f9c9-112">Next, the **CreateDecryptor** method from the **RijndaelManaged** class is passed the same key and IV that was used for encryption and is then passed to the **CryptoStream** constructor.</span></span> <span data-ttu-id="6f9c9-113">Nakonec je výčet **CryptoStreamMode. Read** předán konstruktoru **CryptoStream** , který určuje přístup pro čtení ke streamu.</span><span class="sxs-lookup"><span data-stu-id="6f9c9-113">Finally, the **CryptoStreamMode.Read** enumeration is passed to the **CryptoStream** constructor to specify read access to the stream.</span></span>

```vb
Dim rmCrypto As New RijndaelManaged()
Dim cryptStream As New CryptoStream(myStream, rmCrypto.CreateDecryptor(rmCrypto.Key, rmCrypto.IV), CryptoStreamMode.Read)
```

```csharp
RijndaelManaged rmCrypto = new RijndaelManaged();
CryptoStream cryptStream = new CryptoStream(myStream, rmCrypto.CreateDecryptor(Key, IV), CryptoStreamMode.Read);
```

<span data-ttu-id="6f9c9-114">Následující příklad ukazuje celý proces vytvoření datového proudu, dešifrování datového proudu, čtení z datového proudu a zavření datových proudů.</span><span class="sxs-lookup"><span data-stu-id="6f9c9-114">The following example shows the entire process of creating a stream, decrypting the stream, reading from the stream, and closing the streams.</span></span> <span data-ttu-id="6f9c9-115">Vytvoří se objekt <xref:System.Net.Sockets.TcpListener>, který inicializuje síťový datový proud, když se vytvoří připojení k naslouchajícímu objektu.</span><span class="sxs-lookup"><span data-stu-id="6f9c9-115">A <xref:System.Net.Sockets.TcpListener> object is created that initializes a network stream when a connection to the listening object is made.</span></span> <span data-ttu-id="6f9c9-116">Síťový datový proud je poté dešifrován pomocí třídy **CryptoStream** a třídy **RijndaelManaged** .</span><span class="sxs-lookup"><span data-stu-id="6f9c9-116">The network stream is then decrypted using the **CryptoStream** class and the **RijndaelManaged** class.</span></span> <span data-ttu-id="6f9c9-117">Tento příklad předpokládá, že klíč a hodnoty IV byly buď úspěšně přeneseny nebo dříve odsouhlaseny.</span><span class="sxs-lookup"><span data-stu-id="6f9c9-117">This example assumes that the key and IV values have been either successfully transferred or previously agreed upon.</span></span> <span data-ttu-id="6f9c9-118">Nezobrazuje kód potřebný k šifrování a přenos těchto hodnot.</span><span class="sxs-lookup"><span data-stu-id="6f9c9-118">It does not show the code needed to encrypt and transfer these values.</span></span>

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

<span data-ttu-id="6f9c9-119">Aby předchozí ukázka fungovala, musí být na naslouchací proces provedeno šifrované připojení.</span><span class="sxs-lookup"><span data-stu-id="6f9c9-119">For the previous sample to work, an encrypted connection must be made to the listener.</span></span> <span data-ttu-id="6f9c9-120">Připojení musí používat stejný klíč, IV a algoritmus, který se používá v naslouchací službě.</span><span class="sxs-lookup"><span data-stu-id="6f9c9-120">The connection must use the same key, IV, and algorithm used in the listener.</span></span> <span data-ttu-id="6f9c9-121">Pokud je takové připojení vytvořeno, zpráva je dešifrována a zobrazena v konzole nástroje.</span><span class="sxs-lookup"><span data-stu-id="6f9c9-121">If such a connection is made, the message is decrypted and displayed to the console.</span></span>

## <a name="asymmetric-decryption"></a><span data-ttu-id="6f9c9-122">Asymetrické dešifrování</span><span class="sxs-lookup"><span data-stu-id="6f9c9-122">Asymmetric Decryption</span></span>

<span data-ttu-id="6f9c9-123">Strana (strana A) obvykle generuje veřejný i privátní klíč a ukládá klíč buď do paměti, nebo do kontejneru kryptografických klíčů.</span><span class="sxs-lookup"><span data-stu-id="6f9c9-123">Typically, a party (party A) generates both a public and private key and stores the key either in memory or in a cryptographic key container.</span></span> <span data-ttu-id="6f9c9-124">Strana A pak pošle veřejný klíč druhé straně (smluvní straně B).</span><span class="sxs-lookup"><span data-stu-id="6f9c9-124">Party A then sends the public key to another party (party B).</span></span> <span data-ttu-id="6f9c9-125">Když strana B použije veřejný klíč, zašifruje data a pošle je zpátky do strany A. Po přijetí dat ji strana dešifruje pomocí privátního klíče, který odpovídá.</span><span class="sxs-lookup"><span data-stu-id="6f9c9-125">Using the public key, party B encrypts data and sends the data back to party A. After receiving the data, party A decrypts it using the private key that corresponds.</span></span> <span data-ttu-id="6f9c9-126">Dešifrování bude úspěšné pouze v případě, že strana A používá privátní klíč, který odpovídá veřejnému klíči B, který se používá k šifrování dat.</span><span class="sxs-lookup"><span data-stu-id="6f9c9-126">Decryption will be successful only if party A uses the private key that corresponds to the public key Party B used to encrypt the data.</span></span>

<span data-ttu-id="6f9c9-127">Informace o tom, jak uložit asymetrický klíč do kontejneru zabezpečeného kryptografického klíče a jak později získat asymetrický klíč, najdete v tématu [Postupy: ukládání asymetrických klíčů v kontejneru klíčů](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).</span><span class="sxs-lookup"><span data-stu-id="6f9c9-127">For information on how to store an asymmetric key in secure cryptographic key container and how to later retrieve the asymmetric key, see [How to: Store Asymmetric Keys in a Key Container](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>

<span data-ttu-id="6f9c9-128">Následující příklad znázorňuje dešifrování dvou polí bajtů, které reprezentují symetrický klíč a IV.</span><span class="sxs-lookup"><span data-stu-id="6f9c9-128">The following example illustrates the decryption of two arrays of bytes that represent a symmetric key and IV.</span></span> <span data-ttu-id="6f9c9-129">Informace o tom, jak extrahovat asymetrický veřejný klíč z objektu <xref:System.Security.Cryptography.RSACryptoServiceProvider> ve formátu, který lze snadno odeslat třetí straně, najdete v tématu [šifrování dat](../../../docs/standard/security/encrypting-data.md).</span><span class="sxs-lookup"><span data-stu-id="6f9c9-129">For information on how to extract the asymmetric public key from the <xref:System.Security.Cryptography.RSACryptoServiceProvider> object in a format that you can easily send to a third party, see [Encrypting Data](../../../docs/standard/security/encrypting-data.md).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6f9c9-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6f9c9-130">See also</span></span>

- [<span data-ttu-id="6f9c9-131">Generování klíčů pro šifrování a dešifrování</span><span class="sxs-lookup"><span data-stu-id="6f9c9-131">Generating Keys for Encryption and Decryption</span></span>](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="6f9c9-132">Šifrování dat</span><span class="sxs-lookup"><span data-stu-id="6f9c9-132">Encrypting Data</span></span>](../../../docs/standard/security/encrypting-data.md)
- [<span data-ttu-id="6f9c9-133">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="6f9c9-133">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
