---
title: Dešifrování dat
description: Naučte se, jak dešifrovat data v .NET pomocí symetrického algoritmu nebo asymetrického algoritmu.
ms.date: 07/16/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [.NET], decryption
- symmetric decryption
- asymmetric decryption
- decryption
ms.assetid: 9b266b6c-a9b2-4d20-afd8-b3a0d8fd48a0
ms.openlocfilehash: 2ba4c3ba43d688aeb66c67ec3f94f4a503d47892
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556979"
---
# <a name="decrypting-data"></a><span data-ttu-id="628eb-103">Dešifrování dat</span><span class="sxs-lookup"><span data-stu-id="628eb-103">Decrypting Data</span></span>

<span data-ttu-id="628eb-104">Dešifrování je reverzní operace šifrování.</span><span class="sxs-lookup"><span data-stu-id="628eb-104">Decryption is the reverse operation of encryption.</span></span> <span data-ttu-id="628eb-105">U šifrování tajného klíče je nutné znát klíč i IV, které byly použity k zašifrování dat.</span><span class="sxs-lookup"><span data-stu-id="628eb-105">For secret-key encryption, you must know both the key and IV that were used to encrypt the data.</span></span> <span data-ttu-id="628eb-106">U šifrování veřejného klíče je nutné znát buď veřejný klíč (Pokud byla data zašifrovaná pomocí privátního klíče), nebo privátní klíč (Pokud byla data zašifrovaná pomocí veřejného klíče).</span><span class="sxs-lookup"><span data-stu-id="628eb-106">For public-key encryption, you must know either the public key (if the data was encrypted using the private key) or the private key (if the data was encrypted using the public key).</span></span>

## <a name="symmetric-decryption"></a><span data-ttu-id="628eb-107">Symetrické dešifrování</span><span class="sxs-lookup"><span data-stu-id="628eb-107">Symmetric Decryption</span></span>

<span data-ttu-id="628eb-108">Dešifrování dat šifrovaných pomocí symetrických algoritmů je podobné procesu použitému k šifrování dat pomocí symetrických algoritmů.</span><span class="sxs-lookup"><span data-stu-id="628eb-108">The decryption of data encrypted with symmetric algorithms is similar to the process used to encrypt data with symmetric algorithms.</span></span> <span data-ttu-id="628eb-109"><xref:System.Security.Cryptography.CryptoStream>Třída se používá spolu se symetrickými třídami kryptografie poskytovanými rozhraním .NET k dešifrování dat přečtených z libovolného spravovaného objektu streamu.</span><span class="sxs-lookup"><span data-stu-id="628eb-109">The <xref:System.Security.Cryptography.CryptoStream> class is used with symmetric cryptography classes provided by .NET to decrypt data read from any managed stream object.</span></span>

<span data-ttu-id="628eb-110">Následující příklad ukazuje, jak vytvořit novou instanci výchozí třídy implementace pro <xref:System.Security.Cryptography.Aes> algoritmus.</span><span class="sxs-lookup"><span data-stu-id="628eb-110">The following example illustrates how to create a new instance of the default implementation class for the <xref:System.Security.Cryptography.Aes> algorithm.</span></span> <span data-ttu-id="628eb-111">Instance se používá k dešifrování <xref:System.Security.Cryptography.CryptoStream> objektu.</span><span class="sxs-lookup"><span data-stu-id="628eb-111">The instance is used to perform decryption on a <xref:System.Security.Cryptography.CryptoStream> object.</span></span> <span data-ttu-id="628eb-112">Tento příklad nejprve vytvoří novou instanci třídy implementace **AES** .</span><span class="sxs-lookup"><span data-stu-id="628eb-112">This example first creates a new instance of the **Aes** implementation class.</span></span> <span data-ttu-id="628eb-113">Dále vytvoří objekt **CryptoStream** a inicializuje jej na hodnotu spravovaného datového proudu `myStream` .</span><span class="sxs-lookup"><span data-stu-id="628eb-113">Next it creates a **CryptoStream** object and initializes it to the value of a managed stream called `myStream`.</span></span> <span data-ttu-id="628eb-114">Dále metoda **CreateDecryptor** z třídy **AES** předává stejný klíč a IV, který byl použit pro šifrování a je pak předán konstruktoru **CryptoStream** .</span><span class="sxs-lookup"><span data-stu-id="628eb-114">Next, the **CreateDecryptor** method from the **Aes** class is passed the same key and IV that was used for encryption and is then passed to the **CryptoStream** constructor.</span></span>

```vb
Dim aes As Aes = Aes.Create()
Dim cryptStream As New CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read)
```

```csharp
Aes aes = Aes.Create();
CryptoStream cryptStream = new CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read);
```

<span data-ttu-id="628eb-115">Následující příklad ukazuje celý proces vytvoření datového proudu, dešifrování datového proudu, čtení z datového proudu a zavření datových proudů.</span><span class="sxs-lookup"><span data-stu-id="628eb-115">The following example shows the entire process of creating a stream, decrypting the stream, reading from the stream, and closing the streams.</span></span> <span data-ttu-id="628eb-116">Vytvoří se objekt datového proudu souboru, který přečte soubor s názvem *TestData.txt*.</span><span class="sxs-lookup"><span data-stu-id="628eb-116">A file stream object is created that reads a file named *TestData.txt*.</span></span> <span data-ttu-id="628eb-117">Datový proud souboru je poté dešifrován pomocí třídy **CryptoStream** a třídy **AES** .</span><span class="sxs-lookup"><span data-stu-id="628eb-117">The file stream is then decrypted using the **CryptoStream** class and the **Aes** class.</span></span> <span data-ttu-id="628eb-118">Tento příklad určuje klíče a hodnoty IV, které se používají v příkladu symetrického šifrování pro [šifrování dat](encrypting-data.md).</span><span class="sxs-lookup"><span data-stu-id="628eb-118">This example specifies key and IV values that are used in the symmetric encryption example for [Encrypting Data](encrypting-data.md).</span></span> <span data-ttu-id="628eb-119">Nezobrazuje kód potřebný k šifrování a přenos těchto hodnot.</span><span class="sxs-lookup"><span data-stu-id="628eb-119">It does not show the code needed to encrypt and transfer these values.</span></span>

```vb
Imports System
Imports System.IO
Imports System.Security.Cryptography

Module Module1
    Sub Main()
            'The key and IV must be the same values that were used
            'to encrypt the stream.
            Dim key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}
            Dim iv As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}
        Try
            'Create a file stream.
            Dim myStream As FileStream = new FileStream("TestData.txt", FileMode.Open)

            'Create a new instance of the default Aes implementation class
            'and decrypt the stream.
            Dim aes As Aes = Aes.Create()

            'Create an instance of the CryptoStream class, pass it the file stream, and decrypt
            'it with the Rijndael class using the key and IV.
            Dim cryptStream As New CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read)

            'Read the stream.
            Dim sReader As New StreamReader(cryptStream)

            'Display the message.
            Console.WriteLine("The decrypted original message: {0}", sReader.ReadToEnd())

            'Close the streams.
            sReader.Close()
            myStream.Close()
            'Catch any exceptions.
        Catch
            Console.WriteLine("The decryption Failed.")
            Throw
        End Try
    End Sub
End Module
```

```csharp
using System;
using System.IO;
using System.Security.Cryptography;

class Class1
{
    static void Main(string[] args)
    {
        //The key and IV must be the same values that were used
        //to encrypt the stream.
        byte[] key = { 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16 };
        byte[] iv = { 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16 };
        try
        {
            //Create a file stream.
            FileStream myStream = new FileStream("TestData.txt", FileMode.Open);

            //Create a new instance of the default Aes implementation class
            Aes aes = Aes.Create();

            //Create a CryptoStream, pass it the file stream, and decrypt
            //it with the Aes class using the key and IV.
            CryptoStream cryptStream = new CryptoStream(
               myStream,
               aes.CreateDecryptor(key, iv),
               CryptoStreamMode.Read);

            //Read the stream.
            StreamReader sReader = new StreamReader(cryptStream);

            //Display the message.
            Console.WriteLine("The decrypted original message: {0}", sReader.ReadToEnd());

            //Close the streams.
            sReader.Close();
            myStream.Close();
        }
        //Catch any exceptions.
        catch
        {
            Console.WriteLine("The decryption failed.");
            throw;
        }
    }
}
```

<span data-ttu-id="628eb-120">V předchozím příkladu se používá stejný klíč, IV a algoritmus, který se používá v příkladu symetrického šifrování pro [šifrování dat](encrypting-data.md).</span><span class="sxs-lookup"><span data-stu-id="628eb-120">The preceding example uses the same key, IV, and algorithm used in the symmetric encryption example for [Encrypting Data](encrypting-data.md).</span></span> <span data-ttu-id="628eb-121">Dešifruje soubor *TestData.txt* , který je vytvořen tímto příkladem, a zobrazí původní text v konzole nástroje.</span><span class="sxs-lookup"><span data-stu-id="628eb-121">It decrypts the *TestData.txt* file that is created by that example and displays the original text on the console.</span></span>

## <a name="asymmetric-decryption"></a><span data-ttu-id="628eb-122">Asymetrické dešifrování</span><span class="sxs-lookup"><span data-stu-id="628eb-122">Asymmetric Decryption</span></span>

<span data-ttu-id="628eb-123">Strana (strana A) obvykle generuje veřejný i privátní klíč a ukládá klíč buď do paměti, nebo do kontejneru kryptografických klíčů.</span><span class="sxs-lookup"><span data-stu-id="628eb-123">Typically, a party (party A) generates both a public and private key and stores the key either in memory or in a cryptographic key container.</span></span> <span data-ttu-id="628eb-124">Strana A pak pošle veřejný klíč druhé straně (smluvní straně B).</span><span class="sxs-lookup"><span data-stu-id="628eb-124">Party A then sends the public key to another party (party B).</span></span> <span data-ttu-id="628eb-125">Když strana B použije veřejný klíč, zašifruje data a pošle je zpátky do strany A. Po přijetí dat ji strana dešifruje pomocí privátního klíče, který odpovídá.</span><span class="sxs-lookup"><span data-stu-id="628eb-125">Using the public key, party B encrypts data and sends the data back to party A. After receiving the data, party A decrypts it using the private key that corresponds.</span></span> <span data-ttu-id="628eb-126">Dešifrování bude úspěšné pouze v případě, že strana A používá privátní klíč, který odpovídá veřejnému klíči B, který se používá k šifrování dat.</span><span class="sxs-lookup"><span data-stu-id="628eb-126">Decryption will be successful only if party A uses the private key that corresponds to the public key Party B used to encrypt the data.</span></span>

<span data-ttu-id="628eb-127">Informace o tom, jak uložit asymetrický klíč do kontejneru zabezpečeného kryptografického klíče a jak později získat asymetrický klíč, najdete v tématu [Postupy: ukládání asymetrických klíčů v kontejneru klíčů](how-to-store-asymmetric-keys-in-a-key-container.md).</span><span class="sxs-lookup"><span data-stu-id="628eb-127">For information on how to store an asymmetric key in secure cryptographic key container and how to later retrieve the asymmetric key, see [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>

<span data-ttu-id="628eb-128">Následující příklad znázorňuje dešifrování dvou polí bajtů, které reprezentují symetrický klíč a IV.</span><span class="sxs-lookup"><span data-stu-id="628eb-128">The following example illustrates the decryption of two arrays of bytes that represent a symmetric key and IV.</span></span> <span data-ttu-id="628eb-129">Informace o tom, jak extrahovat asymetrický veřejný klíč z <xref:System.Security.Cryptography.RSA> objektu ve formátu, který lze snadno odeslat třetí straně, najdete v tématu [šifrování dat](encrypting-data.md).</span><span class="sxs-lookup"><span data-stu-id="628eb-129">For information on how to extract the asymmetric public key from the <xref:System.Security.Cryptography.RSA> object in a format that you can easily send to a third party, see [Encrypting Data](encrypting-data.md).</span></span>

```vb
'Create a new instance of the RSA class.
Dim rsa As RSA = RSA.Create()

' Export the public key information and send it to a third party.
' Wait for the third party to encrypt some data and send it back.

'Decrypt the symmetric key and IV.
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, RSAEncryptionPadding.Pkcs1)
symmetricIV = rsa.Decrypt(encryptedSymmetricIV, RSAEncryptionPadding.Pkcs1)
```

```csharp
//Create a new instance of the RSA class.
RSA rsa = RSA.Create();

// Export the public key information and send it to a third party.
// Wait for the third party to encrypt some data and send it back.

//Decrypt the symmetric key and IV.
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, RSAEncryptionPadding.Pkcs1);
symmetricIV = rsa.Decrypt(encryptedSymmetricIV , RSAEncryptionPadding.Pkcs1);
```

## <a name="see-also"></a><span data-ttu-id="628eb-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="628eb-130">See also</span></span>

- [<span data-ttu-id="628eb-131">Generování klíčů pro šifrování a dešifrování</span><span class="sxs-lookup"><span data-stu-id="628eb-131">Generating Keys for Encryption and Decryption</span></span>](generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="628eb-132">Šifrování dat</span><span class="sxs-lookup"><span data-stu-id="628eb-132">Encrypting Data</span></span>](encrypting-data.md)
- [<span data-ttu-id="628eb-133">Šifrovací služby</span><span class="sxs-lookup"><span data-stu-id="628eb-133">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="628eb-134">Kryptografický model</span><span class="sxs-lookup"><span data-stu-id="628eb-134">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="628eb-135">Kryptografie pro různé platformy</span><span class="sxs-lookup"><span data-stu-id="628eb-135">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="628eb-136">Ohrožení zabezpečení časování u symetrického dešifrování pomocí odsazení v režimu CBC</span><span class="sxs-lookup"><span data-stu-id="628eb-136">Timing vulnerabilities with CBC-mode symmetric decryption using padding</span></span>](vulnerabilities-cbc-mode.md)
- [<span data-ttu-id="628eb-137">Ochrana dat ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="628eb-137">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
