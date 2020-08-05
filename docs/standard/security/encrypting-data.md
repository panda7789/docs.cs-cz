---
title: Šifrování dat
description: Naučte se šifrovat data v .NET pomocí symetrického algoritmu nebo asymetrického algoritmu.
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encryption [.NET], symmetric
- symmetric encryption
- cryptography [.NET], asymmetric
- asymmetric encryption
ms.assetid: 7ecce51f-db5f-4bd4-9321-cceb6fcb2a77
ms.openlocfilehash: 8a8b5988a13ab571284b08c7aaece3542467aa71
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556966"
---
# <a name="encrypting-data"></a><span data-ttu-id="29d95-103">Šifrování dat</span><span class="sxs-lookup"><span data-stu-id="29d95-103">Encrypting Data</span></span>

<span data-ttu-id="29d95-104">Symetrické šifrování a asymetrické šifrování se provádí pomocí různých procesů.</span><span class="sxs-lookup"><span data-stu-id="29d95-104">Symmetric encryption and asymmetric encryption are performed using different processes.</span></span> <span data-ttu-id="29d95-105">Symetrické šifrování se provádí na datových proudech a je proto užitečné pro šifrování velkých objemů dat.</span><span class="sxs-lookup"><span data-stu-id="29d95-105">Symmetric encryption is performed on streams and is therefore useful to encrypt large amounts of data.</span></span> <span data-ttu-id="29d95-106">Asymetrické šifrování se provádí na malém počtu bajtů a je proto užitečné jenom pro malé objemy dat.</span><span class="sxs-lookup"><span data-stu-id="29d95-106">Asymmetric encryption is performed on a small number of bytes and is therefore useful only for small amounts of data.</span></span>  
  
## <a name="symmetric-encryption"></a><span data-ttu-id="29d95-107">Symetrické šifrování</span><span class="sxs-lookup"><span data-stu-id="29d95-107">Symmetric Encryption</span></span>  

<span data-ttu-id="29d95-108">Spravované třídy symetrického kryptografie se používají se speciální třídou streamu nazvanou a <xref:System.Security.Cryptography.CryptoStream> , která šifruje data čtená do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="29d95-108">The managed symmetric cryptography classes are used with a special stream class called a <xref:System.Security.Cryptography.CryptoStream> that encrypts data read into the stream.</span></span> <span data-ttu-id="29d95-109">Třída **CryptoStream** je inicializována se třídou spravovaného datového proudu, třídou, která implementuje <xref:System.Security.Cryptography.ICryptoTransform> rozhraní (vytvořené z třídy, která implementuje kryptografický algoritmus), a <xref:System.Security.Cryptography.CryptoStreamMode> výčtem, který popisuje typ přístupu povoleného pro třídu **CryptoStream**.</span><span class="sxs-lookup"><span data-stu-id="29d95-109">The **CryptoStream** class is initialized with a managed stream class, a class that implements the <xref:System.Security.Cryptography.ICryptoTransform> interface (created from a class that implements a cryptographic algorithm), and a <xref:System.Security.Cryptography.CryptoStreamMode> enumeration that describes the type of access permitted to the **CryptoStream**.</span></span> <span data-ttu-id="29d95-110">Třídu **CryptoStream** lze inicializovat pomocí libovolné třídy, která je odvozena od <xref:System.IO.Stream> třídy, včetně <xref:System.IO.FileStream> , <xref:System.IO.MemoryStream> a <xref:System.Net.Sockets.NetworkStream> .</span><span class="sxs-lookup"><span data-stu-id="29d95-110">The **CryptoStream** class can be initialized using any class that derives from the <xref:System.IO.Stream> class, including <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, and <xref:System.Net.Sockets.NetworkStream>.</span></span> <span data-ttu-id="29d95-111">Pomocí těchto tříd můžete provádět symetrické šifrování u nejrůznějších objektů streamu.</span><span class="sxs-lookup"><span data-stu-id="29d95-111">Using these classes, you can perform symmetric encryption on a variety of stream objects.</span></span>  
  
<span data-ttu-id="29d95-112">Následující příklad ukazuje, jak vytvořit novou instanci výchozí třídy implementace pro <xref:System.Security.Cryptography.Aes> algoritmus.</span><span class="sxs-lookup"><span data-stu-id="29d95-112">The following example illustrates how to create a new instance of the default implementation class for the <xref:System.Security.Cryptography.Aes> algorithm.</span></span> <span data-ttu-id="29d95-113">Instance se používá k šifrování u třídy **CryptoStream** .</span><span class="sxs-lookup"><span data-stu-id="29d95-113">The instance is used to perform encryption on a **CryptoStream** class.</span></span> <span data-ttu-id="29d95-114">V tomto příkladu je objekt **CryptoStream** inicializován pomocí objektu datového proudu s názvem `myStream` , který může být jakýkoli typ spravovaného datového proudu.</span><span class="sxs-lookup"><span data-stu-id="29d95-114">In this example, the **CryptoStream** is initialized with a stream object called `myStream` that can be any type of managed stream.</span></span> <span data-ttu-id="29d95-115">Metodě **CreateEncryptor** z třídy **AES** je předán klíč a IV, který se používá k šifrování.</span><span class="sxs-lookup"><span data-stu-id="29d95-115">The **CreateEncryptor** method from the **Aes** class is passed the key and IV that are used for encryption.</span></span> <span data-ttu-id="29d95-116">V takovém případě se použije výchozí klíč a hodnota IV vygenerované z `aes` .</span><span class="sxs-lookup"><span data-stu-id="29d95-116">In this case, the default key and IV generated from `aes` are used.</span></span>
  
```vb  
Dim aes As Aes = Aes.Create()  
Dim cryptStream As New CryptoStream(myStream, aes.CreateEncryptor(key, iv), CryptoStreamMode.Write)  
```  
  
```csharp  
Aes aes = Aes.Create();  
CryptoStream cryptStream = new CryptoStream(myStream, aes.CreateEncryptor(key, iv), CryptoStreamMode.Write);  
```  
  
<span data-ttu-id="29d95-117">Po spuštění tohoto kódu se všechna data zapsaná do objektu **CryptoStream** šifrují pomocí algoritmu AES.</span><span class="sxs-lookup"><span data-stu-id="29d95-117">After this code is executed, any data written to the **CryptoStream** object is encrypted using the AES algorithm.</span></span>  
  
<span data-ttu-id="29d95-118">Následující příklad ukazuje celý proces vytvoření datového proudu, šifrování datového proudu, zápis do datového proudu a zavření datového proudu.</span><span class="sxs-lookup"><span data-stu-id="29d95-118">The following example shows the entire process of creating a stream, encrypting the stream, writing to the stream, and closing the stream.</span></span> <span data-ttu-id="29d95-119">Tento příklad vytvoří datový proud souboru, který je zašifrovaný pomocí třídy **CryptoStream** a třídy **AES** .</span><span class="sxs-lookup"><span data-stu-id="29d95-119">This example creates a file stream that is encrypted using the **CryptoStream** class and the **Aes** class.</span></span> <span data-ttu-id="29d95-120">Do šifrovaného datového proudu s třídou se zapisuje zpráva <xref:System.IO.StreamWriter> .</span><span class="sxs-lookup"><span data-stu-id="29d95-120">A message is written to the encrypted stream with the <xref:System.IO.StreamWriter> class.</span></span>
  
:::code language="csharp" source="snippets/encrypting-data/csharp/aes-encrypt.cs":::
:::code language="vb" source="snippets/encrypting-data/vb/aes-encrypt.vb":::

<span data-ttu-id="29d95-121">Kód šifruje datový proud pomocí symetrického algoritmu AES a zapisuje "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="29d95-121">The code encrypts the stream using the AES symmetric algorithm, and writes "Hello World!"</span></span> <span data-ttu-id="29d95-122">do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="29d95-122">to the stream.</span></span> <span data-ttu-id="29d95-123">Pokud je kód úspěšný, vytvoří zašifrovaný soubor s názvem *TestData.txt* a zobrazí následující text v konzole:</span><span class="sxs-lookup"><span data-stu-id="29d95-123">If the code is successful, it creates an encrypted file named *TestData.txt* and displays the following text to the console:</span></span>  
  
```console  
The text was encrypted.  
```  

<span data-ttu-id="29d95-124">Soubor můžete dešifrovat pomocí příkladu symetrického dešifrování při [dešifrování dat](decrypting-data.md).</span><span class="sxs-lookup"><span data-stu-id="29d95-124">You can decrypt the file by using the symmetric decryption example in [Decrypting Data](decrypting-data.md).</span></span> <span data-ttu-id="29d95-125">Tento příklad a v tomto příkladu určují stejný klíč a IV.</span><span class="sxs-lookup"><span data-stu-id="29d95-125">That example and this example specify the same key and IV.</span></span>

<span data-ttu-id="29d95-126">Nicméně pokud je vyvolána výjimka, kód zobrazí následující text konzole:</span><span class="sxs-lookup"><span data-stu-id="29d95-126">However, if an exception is raised, the code displays the following text to the console:</span></span>  
  
```console  
The encryption failed.  
```

## <a name="asymmetric-encryption"></a><span data-ttu-id="29d95-127">Asymetrické šifrování</span><span class="sxs-lookup"><span data-stu-id="29d95-127">Asymmetric Encryption</span></span>

<span data-ttu-id="29d95-128">Asymetrické algoritmy jsou obvykle používány k šifrování malých objemů dat, jako je například šifrování symetrického klíče a IV.</span><span class="sxs-lookup"><span data-stu-id="29d95-128">Asymmetric algorithms are usually used to encrypt small amounts of data such as the encryption of a symmetric key and IV.</span></span> <span data-ttu-id="29d95-129">Obvykle jednotlivec provádějící asymetrické šifrování používá veřejný klíč generovaný jinou stranou.</span><span class="sxs-lookup"><span data-stu-id="29d95-129">Typically, an individual performing asymmetric encryption uses the public key generated by another party.</span></span> <span data-ttu-id="29d95-130"><xref:System.Security.Cryptography.RSA>Třída je poskytována rozhraním .NET pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="29d95-130">The <xref:System.Security.Cryptography.RSA> class is provided by .NET for this purpose.</span></span>  
  
<span data-ttu-id="29d95-131">Následující příklad používá informace o veřejném klíči k šifrování symetrického klíče a IV.</span><span class="sxs-lookup"><span data-stu-id="29d95-131">The following example uses public key information to encrypt a symmetric key and IV.</span></span> <span data-ttu-id="29d95-132">Jsou inicializována dvě Bajtová pole, která představují veřejný klíč třetí strany.</span><span class="sxs-lookup"><span data-stu-id="29d95-132">Two byte arrays are initialized that represent the public key of a third party.</span></span> <span data-ttu-id="29d95-133"><xref:System.Security.Cryptography.RSAParameters>Objekt je inicializován na tyto hodnoty.</span><span class="sxs-lookup"><span data-stu-id="29d95-133">An <xref:System.Security.Cryptography.RSAParameters> object is initialized to these values.</span></span> <span data-ttu-id="29d95-134">Dále je objekt **RSAParameters** (spolu s veřejným klíčem, který představuje) importován do instance **RSA** pomocí <xref:System.Security.Cryptography.RSA.ImportParameters%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="29d95-134">Next, the **RSAParameters** object (along with the public key it represents) is imported into an **RSA** instance using the <xref:System.Security.Cryptography.RSA.ImportParameters%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="29d95-135">Nakonec se šifrují privátní klíč a IV vytvořené <xref:System.Security.Cryptography.Aes> třídou.</span><span class="sxs-lookup"><span data-stu-id="29d95-135">Finally, the private key and IV created by an <xref:System.Security.Cryptography.Aes> class are encrypted.</span></span> <span data-ttu-id="29d95-136">V tomto příkladu je potřeba, aby systémy měly nainstalované 128 bitového šifrování.</span><span class="sxs-lookup"><span data-stu-id="29d95-136">This example requires systems to have 128-bit encryption installed.</span></span>  
  
```vb  
Imports System
Imports System.Security.Cryptography

Module Module1

    Sub Main()
        'Initialize the byte arrays to the public key information.  
        Dim modulus As Byte() = {214, 46, 220, 83, 160, 73, 40, 39, 201, 155, 19, 202, 3, 11, 191, 178, 56, 74, 90, 36, 248, 103, 18, 144, 170, 163, 145, 87, 54, 61, 34, 220, 222, 207, 137, 149, 173, 14, 92, 120, 206, 222, 158, 28, 40, 24, 30, 16, 175, 108, 128, 35, 230, 118, 40, 121, 113, 125, 216, 130, 11, 24, 90, 48, 194, 240, 105, 44, 76, 34, 57, 249, 228, 125, 80, 38, 9, 136, 29, 117, 207, 139, 168, 181, 85, 137, 126, 10, 126, 242, 120, 247, 121, 8, 100, 12, 201, 171, 38, 226, 193, 180, 190, 117, 177, 87, 143, 242, 213, 11, 44, 180, 113, 93, 106, 99, 179, 68, 175, 211, 164, 116, 64, 148, 226, 254, 172, 147}

        Dim exponent As Byte() = {1, 0, 1}

        'Create values to store encrypted symmetric keys.  
        Dim encryptedSymmetricKey() As Byte
        Dim encryptedSymmetricIV() As Byte

        'Create a new instance of the default RSA implementation class.
        Dim rsa As RSA = RSA.Create()

        'Create a new instance of the RSAParameters structure.  
        Dim rsaKeyInfo As New RSAParameters()

        'Set rsaKeyInfo to the public key values.
        rsaKeyInfo.Modulus = modulus
        rsaKeyInfo.Exponent = exponent

        'Import key parameters into rsa
        rsa.ImportParameters(rsaKeyInfo)

        'Create a new instance of the default Aes implementation class.  
        Dim aes As Aes = Aes.Create()

        'Encrypt the symmetric key and IV.  
        encryptedSymmetricKey = rsa.Encrypt(aes.Key, RSAEncryptionPadding.Pkcs1)
        encryptedSymmetricIV = rsa.Encrypt(aes.IV, RSAEncryptionPadding.Pkcs1)
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
        byte[] modulus = {214,46,220,83,160,73,40,39,201,155,19,202,3,11,191,178,56,
            74,90,36,248,103,18,144,170,163,145,87,54,61,34,220,222,
            207,137,149,173,14,92,120,206,222,158,28,40,24,30,16,175,
            108,128,35,230,118,40,121,113,125,216,130,11,24,90,48,194,
            240,105,44,76,34,57,249,228,125,80,38,9,136,29,117,207,139,
            168,181,85,137,126,10,126,242,120,247,121,8,100,12,201,171,
            38,226,193,180,190,117,177,87,143,242,213,11,44,180,113,93,
            106,99,179,68,175,211,164,116,64,148,226,254,172,147};

        byte[] exponent = { 1, 0, 1 };

        //Create values to store encrypted symmetric keys.  
        byte[] encryptedSymmetricKey;
        byte[] encryptedSymmetricIV;

        //Create a new instance of the RSA class.  
        RSA rsa = RSA.Create();

        //Create a new instance of the RSAParameters structure.  
        RSAParameters rsaKeyInfo = new RSAParameters();

        //Set rsaKeyInfo to the public key values.
        rsaKeyInfo.Modulus = modulus;
        rsaKeyInfo.Exponent = exponent;

        //Import key parameters into rsa.  
        rsa.ImportParameters(rsaKeyInfo);

        //Create a new instance of the default Aes implementation class.  
        Aes aes = Aes.Create();

        //Encrypt the symmetric key and IV.  
        encryptedSymmetricKey = rsa.Encrypt(aes.Key, RSAEncryptionPadding.Pkcs1);
        encryptedSymmetricIV = rsa.Encrypt(aes.IV, RSAEncryptionPadding.Pkcs1);
    }
}
```  
  
## <a name="see-also"></a><span data-ttu-id="29d95-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="29d95-137">See also</span></span>

- [<span data-ttu-id="29d95-138">Generování klíčů pro šifrování a dešifrování</span><span class="sxs-lookup"><span data-stu-id="29d95-138">Generating Keys for Encryption and Decryption</span></span>](generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="29d95-139">Dešifrování dat</span><span class="sxs-lookup"><span data-stu-id="29d95-139">Decrypting Data</span></span>](decrypting-data.md)
- [<span data-ttu-id="29d95-140">Šifrovací služby</span><span class="sxs-lookup"><span data-stu-id="29d95-140">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="29d95-141">Kryptografie pro různé platformy</span><span class="sxs-lookup"><span data-stu-id="29d95-141">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="29d95-142">Ohrožení zabezpečení časování u symetrického dešifrování pomocí odsazení v režimu CBC</span><span class="sxs-lookup"><span data-stu-id="29d95-142">Timing vulnerabilities with CBC-mode symmetric decryption using padding</span></span>](vulnerabilities-cbc-mode.md)
- [<span data-ttu-id="29d95-143">Ochrana dat ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="29d95-143">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
