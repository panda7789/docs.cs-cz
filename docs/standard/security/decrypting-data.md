---
title: "Dešifrování dat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [.NET Framework], decryption
- symmetric decryption
- asymmetric decryption
- decryption
ms.assetid: 9b266b6c-a9b2-4d20-afd8-b3a0d8fd48a0
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6f2ffaeeb8a92dd7ab16b4ba233196230b595af2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="decrypting-data"></a><span data-ttu-id="3526e-102">Dešifrování dat</span><span class="sxs-lookup"><span data-stu-id="3526e-102">Decrypting Data</span></span>
<span data-ttu-id="3526e-103">Dešifrování je reverzní operace šifrování.</span><span class="sxs-lookup"><span data-stu-id="3526e-103">Decryption is the reverse operation of encryption.</span></span> <span data-ttu-id="3526e-104">K šifrování tajného klíče musíte znát IV, které jste použili k šifrování dat i klíč.</span><span class="sxs-lookup"><span data-stu-id="3526e-104">For secret-key encryption, you must know both the key and IV that were used to encrypt the data.</span></span> <span data-ttu-id="3526e-105">K šifrování veřejného klíče musíte znát veřejný klíč (Pokud byla data zašifrována pomocí soukromého klíče) nebo privátní klíč (Pokud byla data zašifrována pomocí veřejného klíče).</span><span class="sxs-lookup"><span data-stu-id="3526e-105">For public-key encryption, you must know either the public key (if the data was encrypted using the private key) or the private key (if the data was encrypted using the public key).</span></span>  
  
## <a name="symmetric-decryption"></a><span data-ttu-id="3526e-106">Symetrické dešifrování</span><span class="sxs-lookup"><span data-stu-id="3526e-106">Symmetric Decryption</span></span>  
 <span data-ttu-id="3526e-107">Dešifrování dat šifrován symetrické algoritmy je podobný proces používaný k šifrování dat symetrickými algoritmy.</span><span class="sxs-lookup"><span data-stu-id="3526e-107">The decryption of data encrypted with symmetric algorithms is similar to the process used to encrypt data with symmetric algorithms.</span></span> <span data-ttu-id="3526e-108"><xref:System.Security.Cryptography.CryptoStream> Třída se používá se symetrické šifrování třídy poskytované rozhraní .NET Framework dešifrovat data načíst z libovolného objektu spravovaného streamu.</span><span class="sxs-lookup"><span data-stu-id="3526e-108">The <xref:System.Security.Cryptography.CryptoStream> class is used with symmetric cryptography classes provided by the .NET Framework to decrypt data read from any managed stream object.</span></span>  
  
 <span data-ttu-id="3526e-109">Následující příklad ukazuje, jak vytvořit novou instanci třídy <xref:System.Security.Cryptography.RijndaelManaged> třídy a použít ho k dešifrování na <xref:System.Security.Cryptography.CryptoStream> objektu.</span><span class="sxs-lookup"><span data-stu-id="3526e-109">The following example illustrates how to create a new instance of the <xref:System.Security.Cryptography.RijndaelManaged> class and use it to perform decryption on a <xref:System.Security.Cryptography.CryptoStream> object.</span></span> <span data-ttu-id="3526e-110">Tento příklad nejprve vytvoří novou instanci třídy **RijndaelManaged** třídy.</span><span class="sxs-lookup"><span data-stu-id="3526e-110">This example first creates a new instance of the **RijndaelManaged** class.</span></span> <span data-ttu-id="3526e-111">Potom vytvoří **CryptoStream** objekt a inicializuje ji na hodnotu spravovaného streamu volat `MyStream`.</span><span class="sxs-lookup"><span data-stu-id="3526e-111">Next it creates a **CryptoStream** object and initializes it to the value of a managed stream called `MyStream`.</span></span> <span data-ttu-id="3526e-112">Dále **CreateDecryptor** metoda z **RijndaelManaged** třída je předán stejný klíč a IV, který byl použit pro šifrování a pak je předána **CryptoStream** konstruktor.</span><span class="sxs-lookup"><span data-stu-id="3526e-112">Next, the **CreateDecryptor** method from the **RijndaelManaged** class is passed the same key and IV that was used for encryption and is then passed to the **CryptoStream** constructor.</span></span> <span data-ttu-id="3526e-113">Nakonec **CryptoStream** výčtu je předán **CryptoStream** konstruktor k zadání přístupu pro čtení do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="3526e-113">Finally, the **CryptoStreamMode.Read** enumeration is passed to the **CryptoStream** constructor to specify read access to the stream.</span></span>  
  
```vb  
Dim RMCrypto As New RijndaelManaged()  
Dim CryptStream As New CryptoStream(MyStream, RMCrypto.CreateDecryptor(RMCrypto.Key, RMCrypto.IV), CryptoStreamMode.Read)  
```  
  
```csharp  
RijndaelManaged RMCrypto = new RijndaelManaged();  
CryptoStream CryptStream = new CryptoStream(MyStream, RMCrypto.CreateDecryptor(Key, IV), CryptoStreamMode.Read);  
```  
  
 <span data-ttu-id="3526e-114">Následující příklad ukazuje celý proces vytváření datového proudu, dešifrování datového proudu, čtení z datového proudu a zavření datových proudů.</span><span class="sxs-lookup"><span data-stu-id="3526e-114">The following example shows the entire process of creating a stream, decrypting the stream, reading from the stream, and closing the streams.</span></span> <span data-ttu-id="3526e-115">A <xref:System.Net.Sockets.TcpListener> je vytvořen objekt, který inicializuje datový proud sítě při připojení k objektu naslouchání.</span><span class="sxs-lookup"><span data-stu-id="3526e-115">A <xref:System.Net.Sockets.TcpListener> object is created that initializes a network stream when a connection to the listening object is made.</span></span> <span data-ttu-id="3526e-116">Datový proud sítě je pak dešifrovat pomocí **CryptoStream** – třída a **RijndaelManaged** třídy.</span><span class="sxs-lookup"><span data-stu-id="3526e-116">The network stream is then decrypted using the **CryptoStream** class and the **RijndaelManaged** class.</span></span> <span data-ttu-id="3526e-117">Tento příklad předpokládá, že klíče a hodnoty IV byly buď úspěšně přenesla nebo dříve schválené.</span><span class="sxs-lookup"><span data-stu-id="3526e-117">This example assumes that the key and IV values have been either successfully transferred or previously agreed upon.</span></span> <span data-ttu-id="3526e-118">Kód potřebný k šifrování a přenos tyto hodnoty nejsou zobrazeny.</span><span class="sxs-lookup"><span data-stu-id="3526e-118">It does not show the code needed to encrypt and transfer these values.</span></span>  
  
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
  
 <span data-ttu-id="3526e-119">Předchozí příklad, fungovat šifrované připojení musí být provedeny pro naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="3526e-119">For the previous sample to work, an encrypted connection must be made to the listener.</span></span> <span data-ttu-id="3526e-120">Připojení k musí používat stejný klíč, IV a algoritmus používaný v naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="3526e-120">The connection must use the same key, IV, and algorithm used in the listener.</span></span> <span data-ttu-id="3526e-121">Pokud se toto připojení, je zpráva dešifrovat a zobrazení v konzole.</span><span class="sxs-lookup"><span data-stu-id="3526e-121">If such a connection is made, the message is decrypted and displayed to the console.</span></span>  
  
## <a name="asymmetric-decryption"></a><span data-ttu-id="3526e-122">Asymetrické dešifrování</span><span class="sxs-lookup"><span data-stu-id="3526e-122">Asymmetric Decryption</span></span>  
 <span data-ttu-id="3526e-123">Obvykle strany (strany A) generuje jak veřejný a privátní klíč a ukládá klíče v paměti nebo v kontejneru kryptografických klíčů.</span><span class="sxs-lookup"><span data-stu-id="3526e-123">Typically, a party (party A) generates both a public and private key and stores the key either in memory or in a cryptographic key container.</span></span>  <span data-ttu-id="3526e-124">Strany, A poté odešle veřejný klíč na druhé straně (straně B).</span><span class="sxs-lookup"><span data-stu-id="3526e-124">Party A then sends the public key to another party (party B).</span></span>  <span data-ttu-id="3526e-125">Pomocí veřejného klíče, strany B šifruje data a odešle data straně a.  Po přijetí dat, strany A dešifruje ji pomocí privátního klíče, který odpovídá.</span><span class="sxs-lookup"><span data-stu-id="3526e-125">Using the public key, party B encrypts data and sends the data back to party A.  After receiving the data, party A decrypts it using the private key that corresponds.</span></span>  <span data-ttu-id="3526e-126">Dešifrování bude úspěšné pouze v případě, že používá privátního klíče, který odpovídá veřejnému klíči strany B používá k šifrování dat A strany.</span><span class="sxs-lookup"><span data-stu-id="3526e-126">Decryption will be successful only if party A uses the private key that corresponds to the public key Party B used to encrypt the data.</span></span>  
  
 <span data-ttu-id="3526e-127">Informace o tom, jak ukládat asymetrického klíče v zabezpečeném kontejneru kryptografických klíčů a jak později načíst asymetrický klíč, najdete v části [postupy: ukládání asymetrických klíčů v kontejneru klíčů](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).</span><span class="sxs-lookup"><span data-stu-id="3526e-127">For information on how to store an asymmetric key in secure cryptographic key container and how to later retrieve the asymmetric key, see [How to: Store Asymmetric Keys in a Key Container](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>  
  
 <span data-ttu-id="3526e-128">Následující příklad ilustruje dešifrování dvě pole bajtů, které představují symetrický klíč a IV.</span><span class="sxs-lookup"><span data-stu-id="3526e-128">The following example illustrates the decryption of two arrays of bytes that represent a symmetric key and IV.</span></span>  <span data-ttu-id="3526e-129">Informace o tom, jak extrahovat asymetrické veřejného klíče z <xref:System.Security.Cryptography.RSACryptoServiceProvider> objekt ve formátu, který lze snadno odeslat třetích stran, najdete v článku [šifrování dat](../../../docs/standard/security/encrypting-data.md).</span><span class="sxs-lookup"><span data-stu-id="3526e-129">For information on how to extract the asymmetric public key from the <xref:System.Security.Cryptography.RSACryptoServiceProvider> object in a format that you can easily send to a third party, see [Encrypting Data](../../../docs/standard/security/encrypting-data.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3526e-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="3526e-130">See Also</span></span>  
 [<span data-ttu-id="3526e-131">Generování klíčů pro šifrování a dešifrování</span><span class="sxs-lookup"><span data-stu-id="3526e-131">Generating Keys for Encryption and Decryption</span></span>](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)  
 [<span data-ttu-id="3526e-132">Šifrování dat</span><span class="sxs-lookup"><span data-stu-id="3526e-132">Encrypting Data</span></span>](../../../docs/standard/security/encrypting-data.md)  
 [<span data-ttu-id="3526e-133">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="3526e-133">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
