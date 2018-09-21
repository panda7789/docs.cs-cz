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
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46531993"
---
# <a name="encrypting-data"></a><span data-ttu-id="5e620-102">Šifrování dat</span><span class="sxs-lookup"><span data-stu-id="5e620-102">Encrypting Data</span></span>
<span data-ttu-id="5e620-103">Symetrické šifrování a asymetrického šifrování se provádí pomocí jiné procesy.</span><span class="sxs-lookup"><span data-stu-id="5e620-103">Symmetric encryption and asymmetric encryption are performed using different processes.</span></span> <span data-ttu-id="5e620-104">Symetrické šifrování se provádí na datové proudy a je proto užitečné k šifrování velkého objemu dat.</span><span class="sxs-lookup"><span data-stu-id="5e620-104">Symmetric encryption is performed on streams and is therefore useful to encrypt large amounts of data.</span></span> <span data-ttu-id="5e620-105">Asymetrické šifrování se provádí na malý počet bajtů a proto je pouze pro malá množství dat užitečné.</span><span class="sxs-lookup"><span data-stu-id="5e620-105">Asymmetric encryption is performed on a small number of bytes and is therefore useful only for small amounts of data.</span></span>  
  
## <a name="symmetric-encryption"></a><span data-ttu-id="5e620-106">Symetrické šifrování</span><span class="sxs-lookup"><span data-stu-id="5e620-106">Symmetric Encryption</span></span>  
 <span data-ttu-id="5e620-107">Třídy spravované symetrického šifrování se používají s zvláštní datový proud třídu s názvem <xref:System.Security.Cryptography.CryptoStream> , který šifruje data načtená do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="5e620-107">The managed symmetric cryptography classes are used with a special stream class called a <xref:System.Security.Cryptography.CryptoStream> that encrypts data read into the stream.</span></span> <span data-ttu-id="5e620-108">**CryptoStream** třída je inicializována s třídou spravovaný datový proud, třída implementuje <xref:System.Security.Cryptography.ICryptoTransform> rozhraní (vytvořené z třídy, která implementuje kryptografický algoritmus) a <xref:System.Security.Cryptography.CryptoStreamMode> výčet, který Popisuje typ přístupu povolený pro **CryptoStream**.</span><span class="sxs-lookup"><span data-stu-id="5e620-108">The **CryptoStream** class is initialized with a managed stream class, a class implements the <xref:System.Security.Cryptography.ICryptoTransform> interface (created from a class that implements a cryptographic algorithm), and a <xref:System.Security.Cryptography.CryptoStreamMode> enumeration that describes the type of access permitted to the **CryptoStream**.</span></span> <span data-ttu-id="5e620-109">**CryptoStream** třídy mohou být inicializovány pomocí libovolné třídy, která je odvozena z <xref:System.IO.Stream> třídy, včetně <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, a <xref:System.Net.Sockets.NetworkStream>.</span><span class="sxs-lookup"><span data-stu-id="5e620-109">The **CryptoStream** class can be initialized using any class that derives from the <xref:System.IO.Stream> class, including <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, and <xref:System.Net.Sockets.NetworkStream>.</span></span> <span data-ttu-id="5e620-110">Použití těchto tříd, můžete provést symetrické šifrování na různých objektů datového proudu.</span><span class="sxs-lookup"><span data-stu-id="5e620-110">Using these classes, you can perform symmetric encryption on a variety of stream objects.</span></span>  
  
 <span data-ttu-id="5e620-111">Následující příklad ukazuje, jak vytvořit novou instanci třídy <xref:System.Security.Cryptography.RijndaelManaged> třídy, která implementuje šifrovacího algoritmu Rijndael a to pomocí provádí šifrování v **CryptoStream** třídy.</span><span class="sxs-lookup"><span data-stu-id="5e620-111">The following example illustrates how to create a new instance of the <xref:System.Security.Cryptography.RijndaelManaged> class, which implements the Rijndael encryption algorithm, and use it to perform encryption on a **CryptoStream** class.</span></span> <span data-ttu-id="5e620-112">V tomto příkladu **CryptoStream** je inicializován s objektem datového proudu, který volá `MyStream` , který může být libovolný typ spravovaný datový proud.</span><span class="sxs-lookup"><span data-stu-id="5e620-112">In this example, the **CryptoStream** is initialized with a stream object called `MyStream` that can be any type of managed stream.</span></span> <span data-ttu-id="5e620-113">**CreateEncryptor** metodu z **RijndaelManaged** třídy je předán klíč a vektor IV, který slouží k šifrování.</span><span class="sxs-lookup"><span data-stu-id="5e620-113">The **CreateEncryptor** method from the **RijndaelManaged** class is passed the key and IV that are used for encryption.</span></span> <span data-ttu-id="5e620-114">V tomto případě výchozí klíč a vektor IV generovány z `RMCrypto` se používají.</span><span class="sxs-lookup"><span data-stu-id="5e620-114">In this case, the default key and IV generated from `RMCrypto` are used.</span></span> <span data-ttu-id="5e620-115">Nakonec **CryptoStreamMode.Write, který specifikuje** je předán přístup pro zápis do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="5e620-115">Finally, the **CryptoStreamMode.Write** is passed, specifying write access to the stream.</span></span>  
  
```vb  
Dim RMCrypto As New RijndaelManaged()  
Dim CryptStream As New CryptoStream(MyStream, RMCrypto.CreateEncryptor(RMCrypto.Key, RMCrypto.IV), CryptoStreamMode.Write)  
```  
  
```csharp  
RijndaelManaged RMCrypto = new RijndaelManaged();  
CryptoStream CryptStream = new CryptoStream(MyStream, RMCrypto.CreateEncryptor(), CryptoStreamMode.Write);  
```  
  
 <span data-ttu-id="5e620-116">Po spuštění tohoto kódu, všechna data zapsána do **CryptoStream** objektu je šifrovaný s použitím algoritmu Rijndael.</span><span class="sxs-lookup"><span data-stu-id="5e620-116">After this code is executed, any data written to the **CryptoStream** object is encrypted using the Rijndael algorithm.</span></span>  
  
 <span data-ttu-id="5e620-117">Následující příklad ukazuje celý proces vytváření datového proudu, šifrování datového proudu, zápis do datového proudu a zavření datového proudu.</span><span class="sxs-lookup"><span data-stu-id="5e620-117">The following example shows the entire process of creating a stream, encrypting the stream, writing to the stream, and closing the stream.</span></span> <span data-ttu-id="5e620-118">Tento příklad vytvoří datový proud sítě, který je šifrovaný s použitím **CryptoStream** třídy a **RijndaelManaged** třídy.</span><span class="sxs-lookup"><span data-stu-id="5e620-118">This example creates a network stream that is encrypted using the **CryptoStream** class and the **RijndaelManaged** class.</span></span> <span data-ttu-id="5e620-119">Zapíše se do šifrovaného datového proudu s <xref:System.IO.StreamWriter> třídy.</span><span class="sxs-lookup"><span data-stu-id="5e620-119">A message is written to the encrypted stream with the <xref:System.IO.StreamWriter> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e620-120">V tomto příkladu můžete také použít k zápisu do souboru.</span><span class="sxs-lookup"><span data-stu-id="5e620-120">You can also use this example to write to a file.</span></span> <span data-ttu-id="5e620-121">K tomuto účelu odstranit <xref:System.Net.Sockets.TcpClient> odkazovat a nahraďte <xref:System.Net.Sockets.NetworkStream> s <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="5e620-121">To do that, delete the <xref:System.Net.Sockets.TcpClient> reference and replace the <xref:System.Net.Sockets.NetworkStream> with a <xref:System.IO.FileStream>.</span></span>  
  
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
  
 <span data-ttu-id="5e620-122">Předchozí příklad proběhl úspěšně, musí být proces, který poslouchá na IP adresu a číslo portu uvedené v <xref:System.Net.Sockets.TcpClient> třídy.</span><span class="sxs-lookup"><span data-stu-id="5e620-122">For the previous example to execute successfully, there must be a process listening on the IP address and port number specified in the <xref:System.Net.Sockets.TcpClient> class.</span></span> <span data-ttu-id="5e620-123">Pokud naslouchací proces existuje, kód se připojit k procesu naslouchání, datového proudu pomocí algoritmu Rijndael symetrický zašifruje a zapíše "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="5e620-123">If a listening process exists, the code will connect to the listening process, encrypt the stream using the Rijndael symmetric algorithm, and write "Hello World!"</span></span> <span data-ttu-id="5e620-124">do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="5e620-124">to the stream.</span></span> <span data-ttu-id="5e620-125">Pokud kód je úspěšná, zobrazí následující text do konzoly:</span><span class="sxs-lookup"><span data-stu-id="5e620-125">If the code is successful, it displays the following text to the console:</span></span>  
  
```  
The message was sent.  
```  
  
 <span data-ttu-id="5e620-126">Ale pokud je nalezen žádný naslouchací proces nebo je vyvolána výjimka, kód zobrazí následující text do konzoly:</span><span class="sxs-lookup"><span data-stu-id="5e620-126">However, if no listening process is found or an exception is raised, the code displays the following text to the console:</span></span>  
  
```  
The connection failed.  
```  
  
## <a name="asymmetric-encryption"></a><span data-ttu-id="5e620-127">Asymetrické šifrování</span><span class="sxs-lookup"><span data-stu-id="5e620-127">Asymmetric Encryption</span></span>  
 <span data-ttu-id="5e620-128">Asymetrické algoritmy se obvykle používají k zašifrování malých objemů dat, třeba šifrování symetrický klíč a vektor IV.</span><span class="sxs-lookup"><span data-stu-id="5e620-128">Asymmetric algorithms are usually used to encrypt small amounts of data such as the encryption of a symmetric key and IV.</span></span> <span data-ttu-id="5e620-129">Obvykle individuální provádění asymetrického šifrování pomocí veřejného klíče generovaný jinou stranou.</span><span class="sxs-lookup"><span data-stu-id="5e620-129">Typically, an individual performing asymmetric encryption uses the public key generated by another party.</span></span> <span data-ttu-id="5e620-130"><xref:System.Security.Cryptography.RSACryptoServiceProvider> Třídy rozhraní .NET Framework poskytuje pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="5e620-130">The <xref:System.Security.Cryptography.RSACryptoServiceProvider> class is provided by the .NET Framework for this purpose.</span></span>  
  
 <span data-ttu-id="5e620-131">Následující příklad používá k šifrování symetrický klíč a vektor IV informace o veřejném klíči.</span><span class="sxs-lookup"><span data-stu-id="5e620-131">The following example uses public key information to encrypt a symmetric key and IV.</span></span> <span data-ttu-id="5e620-132">Dva bajty pole jsou inicializována, které představují veřejný klíč třetích stran.</span><span class="sxs-lookup"><span data-stu-id="5e620-132">Two byte arrays are initialized that represent the public key of a third party.</span></span> <span data-ttu-id="5e620-133"><xref:System.Security.Cryptography.RSAParameters> Objekt je inicializován na tyto hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5e620-133">An <xref:System.Security.Cryptography.RSAParameters> object is initialized to these values.</span></span> <span data-ttu-id="5e620-134">Dále **RSAParameters** objektu (spolu s veřejným klíčem, který představuje), se importují do **RSACryptoServiceProvider** pomocí <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="5e620-134">Next, the **RSAParameters** object (along with the public key it represents) is imported into an **RSACryptoServiceProvider** using the <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5e620-135">Nakonec se privátní klíč a vektor IV vytvořené <xref:System.Security.Cryptography.RijndaelManaged> třídy jsou šifrovaná.</span><span class="sxs-lookup"><span data-stu-id="5e620-135">Finally, the private key and IV created by a <xref:System.Security.Cryptography.RijndaelManaged> class are encrypted.</span></span> <span data-ttu-id="5e620-136">Tento příklad vyžaduje systémy mají nainstalované 128bitové šifrování.</span><span class="sxs-lookup"><span data-stu-id="5e620-136">This example requires systems to have 128-bit encryption installed.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5e620-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5e620-137">See also</span></span>

- [<span data-ttu-id="5e620-138">Generování klíčů pro šifrování a dešifrování</span><span class="sxs-lookup"><span data-stu-id="5e620-138">Generating Keys for Encryption and Decryption</span></span>](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)  
- [<span data-ttu-id="5e620-139">Dešifrování dat</span><span class="sxs-lookup"><span data-stu-id="5e620-139">Decrypting Data</span></span>](../../../docs/standard/security/decrypting-data.md)  
- [<span data-ttu-id="5e620-140">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="5e620-140">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
