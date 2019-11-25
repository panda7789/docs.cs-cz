---
title: Kryptografické podpisy
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- digital signatures
- cryptography [.NET Framework], signatures
- digital signatures, XML signing
- signatures, cryptographic
- digital signatures, generating
- verifying signatures
- generating signatures
- digital signatures, about
- encryption [.NET Framework], signatures
- security [.NET Framework], signatures
- XML signing
- digital signatures, verifying
- signing XML
ms.assetid: aa87cb7f-e608-4a81-948b-c9b8a1225783
author: mairaw
ms.author: mairaw
ms.openlocfilehash: de64af1a4617af39b0ef8e054292a402d6a145e6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350459"
---
# <a name="cryptographic-signatures"></a><span data-ttu-id="e4072-102">Kryptografické podpisy</span><span class="sxs-lookup"><span data-stu-id="e4072-102">Cryptographic Signatures</span></span>

<span data-ttu-id="e4072-103">Cryptographic digital signatures use public key algorithms to provide data integrity.</span><span class="sxs-lookup"><span data-stu-id="e4072-103">Cryptographic digital signatures use public key algorithms to provide data integrity.</span></span> <span data-ttu-id="e4072-104">When you sign data with a digital signature, someone else can verify the signature, and can prove that the data originated from you and was not altered after you signed it.</span><span class="sxs-lookup"><span data-stu-id="e4072-104">When you sign data with a digital signature, someone else can verify the signature, and can prove that the data originated from you and was not altered after you signed it.</span></span> <span data-ttu-id="e4072-105">For more information about digital signatures, see [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md).</span><span class="sxs-lookup"><span data-stu-id="e4072-105">For more information about digital signatures, see [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md).</span></span>

<span data-ttu-id="e4072-106">This topic explains how to generate and verify digital signatures using classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="e4072-106">This topic explains how to generate and verify digital signatures using classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>

## <a name="generating-signatures"></a><span data-ttu-id="e4072-107">Generating Signatures</span><span class="sxs-lookup"><span data-stu-id="e4072-107">Generating Signatures</span></span>

<span data-ttu-id="e4072-108">Digital signatures are usually applied to hash values that represent larger data.</span><span class="sxs-lookup"><span data-stu-id="e4072-108">Digital signatures are usually applied to hash values that represent larger data.</span></span> <span data-ttu-id="e4072-109">The following example applies a digital signature to a hash value.</span><span class="sxs-lookup"><span data-stu-id="e4072-109">The following example applies a digital signature to a hash value.</span></span> <span data-ttu-id="e4072-110">First, a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class is created to generate a public/private key pair.</span><span class="sxs-lookup"><span data-stu-id="e4072-110">First, a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class is created to generate a public/private key pair.</span></span> <span data-ttu-id="e4072-111">Next, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> is passed to a new instance of the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class.</span><span class="sxs-lookup"><span data-stu-id="e4072-111">Next, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> is passed to a new instance of the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class.</span></span> <span data-ttu-id="e4072-112">This transfers the private key to the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, which actually performs the digital signing.</span><span class="sxs-lookup"><span data-stu-id="e4072-112">This transfers the private key to the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, which actually performs the digital signing.</span></span> <span data-ttu-id="e4072-113">Before you can sign the hash code, you must specify a hash algorithm to use.</span><span class="sxs-lookup"><span data-stu-id="e4072-113">Before you can sign the hash code, you must specify a hash algorithm to use.</span></span> <span data-ttu-id="e4072-114">This example uses the SHA1 algorithm.</span><span class="sxs-lookup"><span data-stu-id="e4072-114">This example uses the SHA1 algorithm.</span></span> <span data-ttu-id="e4072-115">Finally, the <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> method is called to perform the signing.</span><span class="sxs-lookup"><span data-stu-id="e4072-115">Finally, the <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> method is called to perform the signing.</span></span>

<span data-ttu-id="e4072-116">Due to collision problems with SHA1, Microsoft recommends SHA256 or better.</span><span class="sxs-lookup"><span data-stu-id="e4072-116">Due to collision problems with SHA1, Microsoft recommends SHA256 or better.</span></span>

```vb
Imports System.Security.Cryptography

Module Module1
    Sub Main()
        'The hash value to sign.
        Dim hashValue As Byte() = {59, 4, 248, 102, 77, 97, 142, 201, 210, 12, 224, 93, 25, 41, 100, 197, 213, 134, 130, 135}

        'The value to hold the signed value.
        Dim signedHashValue() As Byte

        'Generate a public/private key pair.
        Dim rsa As New RSACryptoServiceProvider()

        'Create an RSAPKCS1SignatureFormatter object and pass it
        'the RSACryptoServiceProvider to transfer the private key.
        Dim rsaFormatter As New RSAPKCS1SignatureFormatter(rsa)

        'Set the hash algorithm to SHA1.
        rsaFormatter.SetHashAlgorithm("SHA1")

        'Create a signature for hashValue and assign it to
        'signedHashValue.
        signedHashValue = rsaFormatter.CreateSignature(hashValue)
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
      //The hash value to sign.
      byte[] hashValue = {59,4,248,102,77,97,142,201,210,12,224,93,25,41,100,197,213,134,130,135};

      //The value to hold the signed value.
      byte[] signedHashValue;

      //Generate a public/private key pair.
      RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();

      //Create an RSAPKCS1SignatureFormatter object and pass it the
      //RSACryptoServiceProvider to transfer the private key.
      RSAPKCS1SignatureFormatter rsaFormatter = new RSAPKCS1SignatureFormatter(rsa);

      //Set the hash algorithm to SHA1.
      rsaFormatter.SetHashAlgorithm("SHA1");

      //Create a signature for hashValue and assign it to
      //signedHashValue.
      signedHashValue = rsaFormatter.CreateSignature(hashValue);
   }
}
```

### <a name="signing-xml-files"></a><span data-ttu-id="e4072-117">Signing XML Files</span><span class="sxs-lookup"><span data-stu-id="e4072-117">Signing XML Files</span></span>

<span data-ttu-id="e4072-118">The .NET Framework provides the <xref:System.Security.Cryptography.Xml> namespace, which enables you sign XML.</span><span class="sxs-lookup"><span data-stu-id="e4072-118">The .NET Framework provides the <xref:System.Security.Cryptography.Xml> namespace, which enables you sign XML.</span></span> <span data-ttu-id="e4072-119">Signing XML is important when you want to verify that the XML originates from a certain source.</span><span class="sxs-lookup"><span data-stu-id="e4072-119">Signing XML is important when you want to verify that the XML originates from a certain source.</span></span> <span data-ttu-id="e4072-120">For example, if you are using a stock quote service that uses XML, you can verify the source of the XML if it is signed.</span><span class="sxs-lookup"><span data-stu-id="e4072-120">For example, if you are using a stock quote service that uses XML, you can verify the source of the XML if it is signed.</span></span>

<span data-ttu-id="e4072-121">The classes in this namespace follow the [XML-Signature Syntax and Processing recommendation](https://www.w3.org/TR/xmldsig-core/) from the World Wide Web Consortium.</span><span class="sxs-lookup"><span data-stu-id="e4072-121">The classes in this namespace follow the [XML-Signature Syntax and Processing recommendation](https://www.w3.org/TR/xmldsig-core/) from the World Wide Web Consortium.</span></span>

## <a name="verifying-signatures"></a><span data-ttu-id="e4072-122">Verifying Signatures</span><span class="sxs-lookup"><span data-stu-id="e4072-122">Verifying Signatures</span></span>

<span data-ttu-id="e4072-123">To verify that data was signed by a particular party, you must have the following information:</span><span class="sxs-lookup"><span data-stu-id="e4072-123">To verify that data was signed by a particular party, you must have the following information:</span></span>

- <span data-ttu-id="e4072-124">The public key of the party that signed the data.</span><span class="sxs-lookup"><span data-stu-id="e4072-124">The public key of the party that signed the data.</span></span>

- <span data-ttu-id="e4072-125">The digital signature.</span><span class="sxs-lookup"><span data-stu-id="e4072-125">The digital signature.</span></span>

- <span data-ttu-id="e4072-126">The data that was signed.</span><span class="sxs-lookup"><span data-stu-id="e4072-126">The data that was signed.</span></span>

- <span data-ttu-id="e4072-127">The hash algorithm used by the signer.</span><span class="sxs-lookup"><span data-stu-id="e4072-127">The hash algorithm used by the signer.</span></span>

<span data-ttu-id="e4072-128">To verify a signature signed by the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class, use the <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class.</span><span class="sxs-lookup"><span data-stu-id="e4072-128">To verify a signature signed by the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class, use the <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class.</span></span> <span data-ttu-id="e4072-129">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class must be supplied the public key of the signer.</span><span class="sxs-lookup"><span data-stu-id="e4072-129">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class must be supplied the public key of the signer.</span></span> <span data-ttu-id="e4072-130">You will need the values of the modulus and the exponent to specify the public key.</span><span class="sxs-lookup"><span data-stu-id="e4072-130">You will need the values of the modulus and the exponent to specify the public key.</span></span> <span data-ttu-id="e4072-131">(The party that generated the public/private key pair should provide these values.) First create an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to hold the public key that will verify the signature, and then initialize an <xref:System.Security.Cryptography.RSAParameters> structure to the modulus and exponent values that specify the public key.</span><span class="sxs-lookup"><span data-stu-id="e4072-131">(The party that generated the public/private key pair should provide these values.) First create an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to hold the public key that will verify the signature, and then initialize an <xref:System.Security.Cryptography.RSAParameters> structure to the modulus and exponent values that specify the public key.</span></span>

<span data-ttu-id="e4072-132">The following code shows the creation of an <xref:System.Security.Cryptography.RSAParameters> structure.</span><span class="sxs-lookup"><span data-stu-id="e4072-132">The following code shows the creation of an <xref:System.Security.Cryptography.RSAParameters> structure.</span></span> <span data-ttu-id="e4072-133">The `Modulus` property is set to the value of a byte array called `modulusData` and the `Exponent` property is set to the value of a byte array called `exponentData`.</span><span class="sxs-lookup"><span data-stu-id="e4072-133">The `Modulus` property is set to the value of a byte array called `modulusData` and the `Exponent` property is set to the value of a byte array called `exponentData`.</span></span>

```vb
Dim rsaKeyInfo As RSAParameters
rsaKeyInfo.Modulus = modulusData
rsaKeyInfo.Exponent = exponentData
```

```csharp
RSAParameters rsaKeyInfo;
rsaKeyInfo.Modulus = modulusData;
rsaKeyInfo.Exponent = exponentData;
```

<span data-ttu-id="e4072-134">After you have created the <xref:System.Security.Cryptography.RSAParameters> object, you can initialize a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class to the values specified in <xref:System.Security.Cryptography.RSAParameters>.</span><span class="sxs-lookup"><span data-stu-id="e4072-134">After you have created the <xref:System.Security.Cryptography.RSAParameters> object, you can initialize a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class to the values specified in <xref:System.Security.Cryptography.RSAParameters>.</span></span> <span data-ttu-id="e4072-135">The <xref:System.Security.Cryptography.RSACryptoServiceProvider> is, in turn, passed to the constructor of an <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> to transfer the key.</span><span class="sxs-lookup"><span data-stu-id="e4072-135">The <xref:System.Security.Cryptography.RSACryptoServiceProvider> is, in turn, passed to the constructor of an <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> to transfer the key.</span></span>

<span data-ttu-id="e4072-136">The following example illustrates this process.</span><span class="sxs-lookup"><span data-stu-id="e4072-136">The following example illustrates this process.</span></span> <span data-ttu-id="e4072-137">In this example, `hashValue` and `signedHashValue` are arrays of bytes provided by a remote party.</span><span class="sxs-lookup"><span data-stu-id="e4072-137">In this example, `hashValue` and `signedHashValue` are arrays of bytes provided by a remote party.</span></span> <span data-ttu-id="e4072-138">The remote party has signed the `hashValue` using the SHA1 algorithm, producing the digital signature `signedHashValue`.</span><span class="sxs-lookup"><span data-stu-id="e4072-138">The remote party has signed the `hashValue` using the SHA1 algorithm, producing the digital signature `signedHashValue`.</span></span> <span data-ttu-id="e4072-139">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> method verifies that the digital signature is valid and was used to sign the `hashValue`.</span><span class="sxs-lookup"><span data-stu-id="e4072-139">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> method verifies that the digital signature is valid and was used to sign the `hashValue`.</span></span>

```vb
Dim rsa As New RSACryptoServiceProvider()
rsa.ImportParameters(rsaKeyInfo)
Dim rsaDeformatter As New RSAPKCS1SignatureDeformatter(rsa)
rsaDeformatter.SetHashAlgorithm("SHA1")
If rsaDeformatter.VerifySignature(hashValue, signedHashValue) Then
   Console.WriteLine("The signature is valid.")
Else
   Console.WriteLine("The signature is not valid.")
End If
```

```csharp
RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();
rsa.ImportParameters(rsaKeyInfo);
RSAPKCS1SignatureDeformatter rsaDeformatter = new RSAPKCS1SignatureDeformatter(rsa);
rsaDeformatter.SetHashAlgorithm("SHA1");
if(rsaDeformatter.VerifySignature(hashValue, signedHashValue))
{
   Console.WriteLine("The signature is valid.");
}
else
{
   Console.WriteLine("The signature is not valid.");
}
```

<span data-ttu-id="e4072-140">This code fragment will display "`The signature is valid`" if the signature is valid and "`The signature is not valid`" if it is not.</span><span class="sxs-lookup"><span data-stu-id="e4072-140">This code fragment will display "`The signature is valid`" if the signature is valid and "`The signature is not valid`" if it is not.</span></span>

## <a name="see-also"></a><span data-ttu-id="e4072-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4072-141">See also</span></span>

- [<span data-ttu-id="e4072-142">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="e4072-142">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
