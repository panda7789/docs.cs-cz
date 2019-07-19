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
ms.openlocfilehash: 862d520073dde1b935510bc7c68782c1204c6111
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331649"
---
# <a name="cryptographic-signatures"></a><span data-ttu-id="2af7c-102">Kryptografické podpisy</span><span class="sxs-lookup"><span data-stu-id="2af7c-102">Cryptographic Signatures</span></span>

<a name="top"></a><span data-ttu-id="2af7c-103">Kryptografické digitální podpisy využívají algoritmy veřejného klíče k zajištění integrity dat.</span><span class="sxs-lookup"><span data-stu-id="2af7c-103">Cryptographic digital signatures use public key algorithms to provide data integrity.</span></span> <span data-ttu-id="2af7c-104">Když podepisujete data digitálním podpisem, někdo jiný může podpis ověřit a může prokázat, že data pocházejí z vás a že se po jejím podepsání nezměnila.</span><span class="sxs-lookup"><span data-stu-id="2af7c-104">When you sign data with a digital signature, someone else can verify the signature, and can prove that the data originated from you and was not altered after you signed it.</span></span> <span data-ttu-id="2af7c-105">Další informace o digitálních podpisech najdete v tématu [kryptografické služby](../../../docs/standard/security/cryptographic-services.md).</span><span class="sxs-lookup"><span data-stu-id="2af7c-105">For more information about digital signatures, see [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md).</span></span>

<span data-ttu-id="2af7c-106">Toto téma vysvětluje, jak vygenerovat a ověřit digitální podpisy pomocí tříd v <xref:System.Security.Cryptography?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2af7c-106">This topic explains how to generate and verify digital signatures using classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>

- [<span data-ttu-id="2af7c-107">Generování podpisů</span><span class="sxs-lookup"><span data-stu-id="2af7c-107">Generating Signatures</span></span>](#generate)

- [<span data-ttu-id="2af7c-108">Ověřování podpisů</span><span class="sxs-lookup"><span data-stu-id="2af7c-108">Verifying Signatures</span></span>](#verify)

<a name="generate"></a>

## <a name="generating-signatures"></a><span data-ttu-id="2af7c-109">Generování podpisů</span><span class="sxs-lookup"><span data-stu-id="2af7c-109">Generating Signatures</span></span>

<span data-ttu-id="2af7c-110">Digitální podpisy jsou obvykle aplikovány na hodnoty hash, které představují větší data.</span><span class="sxs-lookup"><span data-stu-id="2af7c-110">Digital signatures are usually applied to hash values that represent larger data.</span></span> <span data-ttu-id="2af7c-111">Následující příklad aplikuje digitální podpis na hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="2af7c-111">The following example applies a digital signature to a hash value.</span></span> <span data-ttu-id="2af7c-112">Nejprve se vytvoří nová instance <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy, která vygeneruje pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="2af7c-112">First, a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class is created to generate a public/private key pair.</span></span> <span data-ttu-id="2af7c-113">Dále je předána do nové instance <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> třídy. <xref:System.Security.Cryptography.RSACryptoServiceProvider></span><span class="sxs-lookup"><span data-stu-id="2af7c-113">Next, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> is passed to a new instance of the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class.</span></span> <span data-ttu-id="2af7c-114">Tím se privátní klíč přenáší do <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, který skutečně provádí digitální podepisování.</span><span class="sxs-lookup"><span data-stu-id="2af7c-114">This transfers the private key to the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, which actually performs the digital signing.</span></span> <span data-ttu-id="2af7c-115">Než budete moci podepsat kód hash, je nutné zadat algoritmus hash, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="2af7c-115">Before you can sign the hash code, you must specify a hash algorithm to use.</span></span> <span data-ttu-id="2af7c-116">V tomto příkladu se používá algoritmus SHA1.</span><span class="sxs-lookup"><span data-stu-id="2af7c-116">This example uses the SHA1 algorithm.</span></span> <span data-ttu-id="2af7c-117">Nakonec je volána metoda pro provedení podepisování. <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A></span><span class="sxs-lookup"><span data-stu-id="2af7c-117">Finally, the <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> method is called to perform the signing.</span></span>

<span data-ttu-id="2af7c-118">Microsoft doporučuje SHA256 nebo lepší kvůli kolizi problémů se SHA1.</span><span class="sxs-lookup"><span data-stu-id="2af7c-118">Due to collision problems with SHA1, Microsoft recommends SHA256 or better.</span></span>

```vb
Imports System
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

### <a name="signing-xml-files"></a><span data-ttu-id="2af7c-119">Podepisování souborů XML</span><span class="sxs-lookup"><span data-stu-id="2af7c-119">Signing XML Files</span></span>

<span data-ttu-id="2af7c-120">.NET Framework poskytuje <xref:System.Security.Cryptography.Xml> obor názvů, který umožňuje podepisování XML.</span><span class="sxs-lookup"><span data-stu-id="2af7c-120">The .NET Framework provides the <xref:System.Security.Cryptography.Xml> namespace, which enables you sign XML.</span></span> <span data-ttu-id="2af7c-121">Podepisování XML je důležité, pokud chcete ověřit, že soubor XML pochází z určitého zdroje.</span><span class="sxs-lookup"><span data-stu-id="2af7c-121">Signing XML is important when you want to verify that the XML originates from a certain source.</span></span> <span data-ttu-id="2af7c-122">Pokud například používáte burzovní službu, která používá XML, můžete ověřit zdroj XML, pokud je podepsaný.</span><span class="sxs-lookup"><span data-stu-id="2af7c-122">For example, if you are using a stock quote service that uses XML, you can verify the source of the XML if it is signed.</span></span>

<span data-ttu-id="2af7c-123">Třídy v tomto oboru názvů následují [syntax XML-Signature a zpracovává doporučení](https://www.w3.org/TR/xmldsig-core/) od konsorcium World Wide Web.</span><span class="sxs-lookup"><span data-stu-id="2af7c-123">The classes in this namespace follow the [XML-Signature Syntax and Processing recommendation](https://www.w3.org/TR/xmldsig-core/) from the World Wide Web Consortium.</span></span>

[<span data-ttu-id="2af7c-124">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="2af7c-124">Back to top</span></span>](#top)

<a name="verify"></a>

## <a name="verifying-signatures"></a><span data-ttu-id="2af7c-125">Ověřování podpisů</span><span class="sxs-lookup"><span data-stu-id="2af7c-125">Verifying Signatures</span></span>

<span data-ttu-id="2af7c-126">Chcete-li ověřit, zda byla data podepsána konkrétní stranou, je nutné mít následující informace:</span><span class="sxs-lookup"><span data-stu-id="2af7c-126">To verify that data was signed by a particular party, you must have the following information:</span></span>

- <span data-ttu-id="2af7c-127">Veřejný klíč strany, která podepsala data.</span><span class="sxs-lookup"><span data-stu-id="2af7c-127">The public key of the party that signed the data.</span></span>

- <span data-ttu-id="2af7c-128">Digitální podpis.</span><span class="sxs-lookup"><span data-stu-id="2af7c-128">The digital signature.</span></span>

- <span data-ttu-id="2af7c-129">Data, která byla podepsána.</span><span class="sxs-lookup"><span data-stu-id="2af7c-129">The data that was signed.</span></span>

- <span data-ttu-id="2af7c-130">Algoritmus hash používaný podepsáním.</span><span class="sxs-lookup"><span data-stu-id="2af7c-130">The hash algorithm used by the signer.</span></span>

<span data-ttu-id="2af7c-131">Chcete-li ověřit podpis podepsaný <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> třídou, <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> použijte třídu.</span><span class="sxs-lookup"><span data-stu-id="2af7c-131">To verify a signature signed by the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class, use the <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class.</span></span> <span data-ttu-id="2af7c-132"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> Třídě musí být dodán veřejný klíč podepsaného.</span><span class="sxs-lookup"><span data-stu-id="2af7c-132">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class must be supplied the public key of the signer.</span></span> <span data-ttu-id="2af7c-133">K určení veřejného klíče budete potřebovat hodnoty zbytku a exponentu.</span><span class="sxs-lookup"><span data-stu-id="2af7c-133">You will need the values of the modulus and the exponent to specify the public key.</span></span> <span data-ttu-id="2af7c-134">(Strana, která vygenerovala pár veřejného a privátního klíče, by měla poskytnout tyto hodnoty.) Nejprve vytvořte <xref:System.Security.Cryptography.RSACryptoServiceProvider> objekt, který bude obsahovat veřejný klíč, který ověří podpis, a poté <xref:System.Security.Cryptography.RSAParameters> inicializuje strukturu na hodnoty modulu a exponentu, které určují veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="2af7c-134">(The party that generated the public/private key pair should provide these values.) First create an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to hold the public key that will verify the signature, and then initialize an <xref:System.Security.Cryptography.RSAParameters> structure to the modulus and exponent values that specify the public key.</span></span>

<span data-ttu-id="2af7c-135">Následující kód ukazuje vytvoření <xref:System.Security.Cryptography.RSAParameters> struktury.</span><span class="sxs-lookup"><span data-stu-id="2af7c-135">The following code shows the creation of an <xref:System.Security.Cryptography.RSAParameters> structure.</span></span> <span data-ttu-id="2af7c-136">Vlastnost je nastavena na hodnotu s názvem `modulusData` bajtového pole a `Exponent` vlastnost je nastavena na hodnotu s názvem `exponentData`bajtového pole. `Modulus`</span><span class="sxs-lookup"><span data-stu-id="2af7c-136">The `Modulus` property is set to the value of a byte array called `modulusData` and the `Exponent` property is set to the value of a byte array called `exponentData`.</span></span>

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

<span data-ttu-id="2af7c-137">Po vytvoření <xref:System.Security.Cryptography.RSAParameters> objektu můžete inicializovat novou instanci <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy na hodnoty, které jsou zadány v <xref:System.Security.Cryptography.RSAParameters>.</span><span class="sxs-lookup"><span data-stu-id="2af7c-137">After you have created the <xref:System.Security.Cryptography.RSAParameters> object, you can initialize a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class to the values specified in <xref:System.Security.Cryptography.RSAParameters>.</span></span> <span data-ttu-id="2af7c-138">Je zase předán do konstruktoru <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> pro přenos klíče. <xref:System.Security.Cryptography.RSACryptoServiceProvider></span><span class="sxs-lookup"><span data-stu-id="2af7c-138">The <xref:System.Security.Cryptography.RSACryptoServiceProvider> is, in turn, passed to the constructor of an <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> to transfer the key.</span></span>

<span data-ttu-id="2af7c-139">Následující příklad znázorňuje tento proces.</span><span class="sxs-lookup"><span data-stu-id="2af7c-139">The following example illustrates this process.</span></span> <span data-ttu-id="2af7c-140">V tomto příkladu `hashValue` `signedHashValue` jsou pole bajtů poskytnuté vzdálenou stranou.</span><span class="sxs-lookup"><span data-stu-id="2af7c-140">In this example, `hashValue` and `signedHashValue` are arrays of bytes provided by a remote party.</span></span> <span data-ttu-id="2af7c-141">Vzdálená strana podepsala certifikát `hashValue` pomocí algoritmu SHA1 a vytvořil digitální podpis. `signedHashValue`</span><span class="sxs-lookup"><span data-stu-id="2af7c-141">The remote party has signed the `hashValue` using the SHA1 algorithm, producing the digital signature `signedHashValue`.</span></span> <span data-ttu-id="2af7c-142">Metoda ověřuje, zda je digitální podpis platný a byl použit k `hashValue`podepsání. <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="2af7c-142">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> method verifies that the digital signature is valid and was used to sign the `hashValue`.</span></span>

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

<span data-ttu-id="2af7c-143">Tento fragment kódu zobrazí "`The signature is valid`", pokud je podpis platný a "`The signature is not valid`", pokud není.</span><span class="sxs-lookup"><span data-stu-id="2af7c-143">This code fragment will display "`The signature is valid`" if the signature is valid and "`The signature is not valid`" if it is not.</span></span>

## <a name="see-also"></a><span data-ttu-id="2af7c-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2af7c-144">See also</span></span>

- [<span data-ttu-id="2af7c-145">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="2af7c-145">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
