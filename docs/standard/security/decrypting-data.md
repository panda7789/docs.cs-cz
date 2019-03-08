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
ms.openlocfilehash: 4cf0ffae2c5803324d4941581855d5dc10224e07
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675339"
---
# <a name="decrypting-data"></a><span data-ttu-id="9ffe1-102">Dešifrování dat</span><span class="sxs-lookup"><span data-stu-id="9ffe1-102">Decrypting Data</span></span>

<span data-ttu-id="9ffe1-103">Dešifrování se zpětná operace šifrování.</span><span class="sxs-lookup"><span data-stu-id="9ffe1-103">Decryption is the reverse operation of encryption.</span></span> <span data-ttu-id="9ffe1-104">K šifrování tajného klíče musíte znát klíč a vektor IV použitý k šifrování dat.</span><span class="sxs-lookup"><span data-stu-id="9ffe1-104">For secret-key encryption, you must know both the key and IV that were used to encrypt the data.</span></span> <span data-ttu-id="9ffe1-105">Pro šifrování s veřejným klíčem je třeba znát veřejného klíče (Pokud byla data zašifrována pomocí soukromého klíče) nebo privátní klíč (Pokud byla data zašifrována pomocí veřejného klíče).</span><span class="sxs-lookup"><span data-stu-id="9ffe1-105">For public-key encryption, you must know either the public key (if the data was encrypted using the private key) or the private key (if the data was encrypted using the public key).</span></span>

## <a name="symmetric-decryption"></a><span data-ttu-id="9ffe1-106">Symetrické dešifrování</span><span class="sxs-lookup"><span data-stu-id="9ffe1-106">Symmetric Decryption</span></span>

<span data-ttu-id="9ffe1-107">Dešifrování data zašifrovaná pomocí symetrických algoritmů je podobný procesu použité k šifrování dat pomocí symetrických algoritmů.</span><span class="sxs-lookup"><span data-stu-id="9ffe1-107">The decryption of data encrypted with symmetric algorithms is similar to the process used to encrypt data with symmetric algorithms.</span></span> <span data-ttu-id="9ffe1-108"><xref:System.Security.Cryptography.CryptoStream> Třída se používá s třídami symetrické šifrování poskytované rozhraní .NET Framework se dešifrovat data načtená z libovolného objektu spravovaný datový proud.</span><span class="sxs-lookup"><span data-stu-id="9ffe1-108">The <xref:System.Security.Cryptography.CryptoStream> class is used with symmetric cryptography classes provided by the .NET Framework to decrypt data read from any managed stream object.</span></span>

<span data-ttu-id="9ffe1-109">Následující příklad ukazuje, jak vytvořit novou instanci třídy <xref:System.Security.Cryptography.RijndaelManaged> třídy a použít ho k dešifrování na <xref:System.Security.Cryptography.CryptoStream> objektu.</span><span class="sxs-lookup"><span data-stu-id="9ffe1-109">The following example illustrates how to create a new instance of the <xref:System.Security.Cryptography.RijndaelManaged> class and use it to perform decryption on a <xref:System.Security.Cryptography.CryptoStream> object.</span></span> <span data-ttu-id="9ffe1-110">Tento příklad nejprve vytvoří novou instanci třídy **RijndaelManaged** třídy.</span><span class="sxs-lookup"><span data-stu-id="9ffe1-110">This example first creates a new instance of the **RijndaelManaged** class.</span></span> <span data-ttu-id="9ffe1-111">Vedle vytváření **CryptoStream** objektu a inicializuje ji na hodnotu spravovaný datový proud volá `myStream`.</span><span class="sxs-lookup"><span data-stu-id="9ffe1-111">Next it creates a **CryptoStream** object and initializes it to the value of a managed stream called `myStream`.</span></span> <span data-ttu-id="9ffe1-112">Dále **CreateDecryptor** metodu z **RijndaelManaged** třídy je předán stejný klíč a vektor IV, který se použil pro šifrování a je pak předán **CryptoStream** konstruktor.</span><span class="sxs-lookup"><span data-stu-id="9ffe1-112">Next, the **CreateDecryptor** method from the **RijndaelManaged** class is passed the same key and IV that was used for encryption and is then passed to the **CryptoStream** constructor.</span></span> <span data-ttu-id="9ffe1-113">Nakonec **CryptoStream** výčtu je předán **CryptoStream** konstruktor k zadání oprávnění ke čtení pro datový proud.</span><span class="sxs-lookup"><span data-stu-id="9ffe1-113">Finally, the **CryptoStreamMode.Read** enumeration is passed to the **CryptoStream** constructor to specify read access to the stream.</span></span>

```vb
Dim rmCrypto As New RijndaelManaged()
Dim cryptStream As New CryptoStream(myStream, rmCrypto.CreateDecryptor(rmCrypto.Key, rmCrypto.IV), CryptoStreamMode.Read)
```

```csharp
RijndaelManaged rmCrypto = new RijndaelManaged();
CryptoStream cryptStream = new CryptoStream(myStream, rmCrypto.CreateDecryptor(Key, IV), CryptoStreamMode.Read);
```

<span data-ttu-id="9ffe1-114">Následující příklad ukazuje celý proces vytváření datového proudu, dešifrování datového proudu, čtení z datového proudu a zavření datových proudů.</span><span class="sxs-lookup"><span data-stu-id="9ffe1-114">The following example shows the entire process of creating a stream, decrypting the stream, reading from the stream, and closing the streams.</span></span> <span data-ttu-id="9ffe1-115">A <xref:System.Net.Sockets.TcpListener> je vytvořen objekt, který inicializuje sítě datového proudu při připojení k naslouchání objektu.</span><span class="sxs-lookup"><span data-stu-id="9ffe1-115">A <xref:System.Net.Sockets.TcpListener> object is created that initializes a network stream when a connection to the listening object is made.</span></span> <span data-ttu-id="9ffe1-116">Datový proud sítě je pak dešifrovat pomocí **CryptoStream** třídy a **RijndaelManaged** třídy.</span><span class="sxs-lookup"><span data-stu-id="9ffe1-116">The network stream is then decrypted using the **CryptoStream** class and the **RijndaelManaged** class.</span></span> <span data-ttu-id="9ffe1-117">Tento příklad předpokládá, že klíč a vektor IV hodnoty byly buď úspěšně převeden nebo dříve dohodnutých.</span><span class="sxs-lookup"><span data-stu-id="9ffe1-117">This example assumes that the key and IV values have been either successfully transferred or previously agreed upon.</span></span> <span data-ttu-id="9ffe1-118">Nezobrazuje se kód potřebný k šifrování a přenést tyto hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9ffe1-118">It does not show the code needed to encrypt and transfer these values.</span></span>

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

<span data-ttu-id="9ffe1-119">Předchozí ukázka fungovala musí provést šifrované připojení k naslouchacímu procesu.</span><span class="sxs-lookup"><span data-stu-id="9ffe1-119">For the previous sample to work, an encrypted connection must be made to the listener.</span></span> <span data-ttu-id="9ffe1-120">Připojení musí používat stejný klíč, IV a algoritmus používaný v naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="9ffe1-120">The connection must use the same key, IV, and algorithm used in the listener.</span></span> <span data-ttu-id="9ffe1-121">Pokud je toto připojení, zpráva se dešifrují a zobrazí v konzole.</span><span class="sxs-lookup"><span data-stu-id="9ffe1-121">If such a connection is made, the message is decrypted and displayed to the console.</span></span>

## <a name="asymmetric-decryption"></a><span data-ttu-id="9ffe1-122">Asymetrické dešifrování</span><span class="sxs-lookup"><span data-stu-id="9ffe1-122">Asymmetric Decryption</span></span>

<span data-ttu-id="9ffe1-123">Strana (stran A) obvykle generuje i veřejného a privátního klíče a uloží klíč v paměti nebo v kontejneru kryptografických klíčů.</span><span class="sxs-lookup"><span data-stu-id="9ffe1-123">Typically, a party (party A) generates both a public and private key and stores the key either in memory or in a cryptographic key container.</span></span> <span data-ttu-id="9ffe1-124">Party, A poté odešle veřejný klíč do jiného (strana B).</span><span class="sxs-lookup"><span data-stu-id="9ffe1-124">Party A then sends the public key to another party (party B).</span></span> <span data-ttu-id="9ffe1-125">Pomocí veřejného klíče, strana B šifruje data a odešle data zpět do strany A. Po přijetí dat, strana A dešifruje ji pomocí soukromého klíče, který odpovídá.</span><span class="sxs-lookup"><span data-stu-id="9ffe1-125">Using the public key, party B encrypts data and sends the data back to party A. After receiving the data, party A decrypts it using the private key that corresponds.</span></span> <span data-ttu-id="9ffe1-126">Dešifrování bude úspěšné pouze v případě, že strana A privátní klíč, který odpovídá veřejnému klíči stran B používá k šifrování dat používá.</span><span class="sxs-lookup"><span data-stu-id="9ffe1-126">Decryption will be successful only if party A uses the private key that corresponds to the public key Party B used to encrypt the data.</span></span>

<span data-ttu-id="9ffe1-127">Informace o způsobu uložení asymetrického klíče v kontejneru zabezpečené kryptografické klíče a jak později načíst asymetrického klíče, naleznete v tématu [jak: Store asymetrického klíče v kontejneru klíčů](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).</span><span class="sxs-lookup"><span data-stu-id="9ffe1-127">For information on how to store an asymmetric key in secure cryptographic key container and how to later retrieve the asymmetric key, see [How to: Store Asymmetric Keys in a Key Container](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>

<span data-ttu-id="9ffe1-128">Následující příklad ukazuje dešifrování dvě pole bajtů, která představuje symetrický klíč a vektor IV.</span><span class="sxs-lookup"><span data-stu-id="9ffe1-128">The following example illustrates the decryption of two arrays of bytes that represent a symmetric key and IV.</span></span> <span data-ttu-id="9ffe1-129">Informace o tom, jak extrahovat asymetrického veřejný klíč z <xref:System.Security.Cryptography.RSACryptoServiceProvider> objektu ve formátu, který můžete snadno odesílat žádné třetí straně, přečtěte si téma [šifrování dat](../../../docs/standard/security/encrypting-data.md).</span><span class="sxs-lookup"><span data-stu-id="9ffe1-129">For information on how to extract the asymmetric public key from the <xref:System.Security.Cryptography.RSACryptoServiceProvider> object in a format that you can easily send to a third party, see [Encrypting Data](../../../docs/standard/security/encrypting-data.md).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9ffe1-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ffe1-130">See also</span></span>

- [<span data-ttu-id="9ffe1-131">Generování klíčů pro šifrování a dešifrování</span><span class="sxs-lookup"><span data-stu-id="9ffe1-131">Generating Keys for Encryption and Decryption</span></span>](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="9ffe1-132">Šifrování dat</span><span class="sxs-lookup"><span data-stu-id="9ffe1-132">Encrypting Data</span></span>](../../../docs/standard/security/encrypting-data.md)
- [<span data-ttu-id="9ffe1-133">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="9ffe1-133">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
