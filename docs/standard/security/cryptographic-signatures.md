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
# <a name="cryptographic-signatures"></a><span data-ttu-id="e1393-102">Kryptografické podpisy</span><span class="sxs-lookup"><span data-stu-id="e1393-102">Cryptographic Signatures</span></span>

<span data-ttu-id="e1393-103">Kryptografické digitální podpisy využívají algoritmy veřejného klíče k zajištění integrity dat.</span><span class="sxs-lookup"><span data-stu-id="e1393-103">Cryptographic digital signatures use public key algorithms to provide data integrity.</span></span> <span data-ttu-id="e1393-104">Když podepisujete data digitálním podpisem, někdo jiný může podpis ověřit a může prokázat, že data pocházejí z vás a že se po jejím podepsání nezměnila.</span><span class="sxs-lookup"><span data-stu-id="e1393-104">When you sign data with a digital signature, someone else can verify the signature, and can prove that the data originated from you and was not altered after you signed it.</span></span> <span data-ttu-id="e1393-105">Další informace o digitálních podpisech najdete v tématu [kryptografické služby](../../../docs/standard/security/cryptographic-services.md).</span><span class="sxs-lookup"><span data-stu-id="e1393-105">For more information about digital signatures, see [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md).</span></span>

<span data-ttu-id="e1393-106">Toto téma vysvětluje, jak vygenerovat a ověřit digitální podpisy pomocí tříd v oboru názvů <xref:System.Security.Cryptography?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e1393-106">This topic explains how to generate and verify digital signatures using classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>

## <a name="generating-signatures"></a><span data-ttu-id="e1393-107">Generování podpisů</span><span class="sxs-lookup"><span data-stu-id="e1393-107">Generating Signatures</span></span>

<span data-ttu-id="e1393-108">Digitální podpisy jsou obvykle aplikovány na hodnoty hash, které představují větší data.</span><span class="sxs-lookup"><span data-stu-id="e1393-108">Digital signatures are usually applied to hash values that represent larger data.</span></span> <span data-ttu-id="e1393-109">Následující příklad aplikuje digitální podpis na hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="e1393-109">The following example applies a digital signature to a hash value.</span></span> <span data-ttu-id="e1393-110">Nejprve je vytvořena nová instance třídy <xref:System.Security.Cryptography.RSACryptoServiceProvider> pro vygenerování páru veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="e1393-110">First, a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class is created to generate a public/private key pair.</span></span> <span data-ttu-id="e1393-111">Dále je <xref:System.Security.Cryptography.RSACryptoServiceProvider> předán nové instanci <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> třídy.</span><span class="sxs-lookup"><span data-stu-id="e1393-111">Next, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> is passed to a new instance of the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class.</span></span> <span data-ttu-id="e1393-112">Tím se privátní klíč přenáší na <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, které skutečně provádí digitální podepisování.</span><span class="sxs-lookup"><span data-stu-id="e1393-112">This transfers the private key to the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, which actually performs the digital signing.</span></span> <span data-ttu-id="e1393-113">Než budete moci podepsat kód hash, je nutné zadat algoritmus hash, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="e1393-113">Before you can sign the hash code, you must specify a hash algorithm to use.</span></span> <span data-ttu-id="e1393-114">V tomto příkladu se používá algoritmus SHA1.</span><span class="sxs-lookup"><span data-stu-id="e1393-114">This example uses the SHA1 algorithm.</span></span> <span data-ttu-id="e1393-115">Nakonec je volána metoda <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> k provedení podepisování.</span><span class="sxs-lookup"><span data-stu-id="e1393-115">Finally, the <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> method is called to perform the signing.</span></span>

<span data-ttu-id="e1393-116">Microsoft doporučuje SHA256 nebo lepší kvůli kolizi problémů se SHA1.</span><span class="sxs-lookup"><span data-stu-id="e1393-116">Due to collision problems with SHA1, Microsoft recommends SHA256 or better.</span></span>

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

### <a name="signing-xml-files"></a><span data-ttu-id="e1393-117">Podepisování souborů XML</span><span class="sxs-lookup"><span data-stu-id="e1393-117">Signing XML Files</span></span>

<span data-ttu-id="e1393-118">.NET Framework poskytuje obor názvů <xref:System.Security.Cryptography.Xml>, který umožňuje podepisování XML.</span><span class="sxs-lookup"><span data-stu-id="e1393-118">The .NET Framework provides the <xref:System.Security.Cryptography.Xml> namespace, which enables you sign XML.</span></span> <span data-ttu-id="e1393-119">Podepisování XML je důležité, pokud chcete ověřit, že soubor XML pochází z určitého zdroje.</span><span class="sxs-lookup"><span data-stu-id="e1393-119">Signing XML is important when you want to verify that the XML originates from a certain source.</span></span> <span data-ttu-id="e1393-120">Pokud například používáte burzovní službu, která používá XML, můžete ověřit zdroj XML, pokud je podepsaný.</span><span class="sxs-lookup"><span data-stu-id="e1393-120">For example, if you are using a stock quote service that uses XML, you can verify the source of the XML if it is signed.</span></span>

<span data-ttu-id="e1393-121">Třídy v tomto oboru názvů následují [syntax XML-Signature a zpracovává doporučení](https://www.w3.org/TR/xmldsig-core/) od konsorcium World Wide Web.</span><span class="sxs-lookup"><span data-stu-id="e1393-121">The classes in this namespace follow the [XML-Signature Syntax and Processing recommendation](https://www.w3.org/TR/xmldsig-core/) from the World Wide Web Consortium.</span></span>

## <a name="verifying-signatures"></a><span data-ttu-id="e1393-122">Ověřování podpisů</span><span class="sxs-lookup"><span data-stu-id="e1393-122">Verifying Signatures</span></span>

<span data-ttu-id="e1393-123">Chcete-li ověřit, zda byla data podepsána konkrétní stranou, je nutné mít následující informace:</span><span class="sxs-lookup"><span data-stu-id="e1393-123">To verify that data was signed by a particular party, you must have the following information:</span></span>

- <span data-ttu-id="e1393-124">Veřejný klíč strany, která podepsala data.</span><span class="sxs-lookup"><span data-stu-id="e1393-124">The public key of the party that signed the data.</span></span>

- <span data-ttu-id="e1393-125">Digitální podpis.</span><span class="sxs-lookup"><span data-stu-id="e1393-125">The digital signature.</span></span>

- <span data-ttu-id="e1393-126">Data, která byla podepsána.</span><span class="sxs-lookup"><span data-stu-id="e1393-126">The data that was signed.</span></span>

- <span data-ttu-id="e1393-127">Algoritmus hash používaný podepsáním.</span><span class="sxs-lookup"><span data-stu-id="e1393-127">The hash algorithm used by the signer.</span></span>

<span data-ttu-id="e1393-128">Chcete-li ověřit podpis podepsaný <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> třídou, použijte třídu <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter>.</span><span class="sxs-lookup"><span data-stu-id="e1393-128">To verify a signature signed by the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class, use the <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class.</span></span> <span data-ttu-id="e1393-129">Třídě <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> musí být dodán veřejný klíč podepsaného.</span><span class="sxs-lookup"><span data-stu-id="e1393-129">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class must be supplied the public key of the signer.</span></span> <span data-ttu-id="e1393-130">K určení veřejného klíče budete potřebovat hodnoty zbytku a exponentu.</span><span class="sxs-lookup"><span data-stu-id="e1393-130">You will need the values of the modulus and the exponent to specify the public key.</span></span> <span data-ttu-id="e1393-131">(Strana, která vygenerovala pár veřejného a privátního klíče, by měla poskytnout tyto hodnoty.) Nejdřív vytvořte objekt <xref:System.Security.Cryptography.RSACryptoServiceProvider>, který bude obsahovat veřejný klíč, který ověří podpis, a pak inicializuje <xref:System.Security.Cryptography.RSAParameters> strukturu na hodnoty modulu a exponentu, které určují veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="e1393-131">(The party that generated the public/private key pair should provide these values.) First create an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to hold the public key that will verify the signature, and then initialize an <xref:System.Security.Cryptography.RSAParameters> structure to the modulus and exponent values that specify the public key.</span></span>

<span data-ttu-id="e1393-132">Následující kód ukazuje vytvoření struktury <xref:System.Security.Cryptography.RSAParameters>.</span><span class="sxs-lookup"><span data-stu-id="e1393-132">The following code shows the creation of an <xref:System.Security.Cryptography.RSAParameters> structure.</span></span> <span data-ttu-id="e1393-133">Vlastnost `Modulus` je nastavena na hodnotu bajtového pole s názvem `modulusData` a vlastnost `Exponent` je nastavena na hodnotu bajtového pole s názvem `exponentData`.</span><span class="sxs-lookup"><span data-stu-id="e1393-133">The `Modulus` property is set to the value of a byte array called `modulusData` and the `Exponent` property is set to the value of a byte array called `exponentData`.</span></span>

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

<span data-ttu-id="e1393-134">Po vytvoření objektu <xref:System.Security.Cryptography.RSAParameters> můžete inicializovat novou instanci <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy na hodnoty zadané v <xref:System.Security.Cryptography.RSAParameters>.</span><span class="sxs-lookup"><span data-stu-id="e1393-134">After you have created the <xref:System.Security.Cryptography.RSAParameters> object, you can initialize a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class to the values specified in <xref:System.Security.Cryptography.RSAParameters>.</span></span> <span data-ttu-id="e1393-135"><xref:System.Security.Cryptography.RSACryptoServiceProvider> je následně předán do konstruktoru <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> pro přenos klíče.</span><span class="sxs-lookup"><span data-stu-id="e1393-135">The <xref:System.Security.Cryptography.RSACryptoServiceProvider> is, in turn, passed to the constructor of an <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> to transfer the key.</span></span>

<span data-ttu-id="e1393-136">Následující příklad znázorňuje tento proces.</span><span class="sxs-lookup"><span data-stu-id="e1393-136">The following example illustrates this process.</span></span> <span data-ttu-id="e1393-137">V tomto příkladu jsou `hashValue` a `signedHashValue` pole bajtů poskytované vzdálenou stranou.</span><span class="sxs-lookup"><span data-stu-id="e1393-137">In this example, `hashValue` and `signedHashValue` are arrays of bytes provided by a remote party.</span></span> <span data-ttu-id="e1393-138">Vzdálená strana podepsala `hashValue` pomocí algoritmu SHA1 a vytvořil `signedHashValue`digitálního podpisu.</span><span class="sxs-lookup"><span data-stu-id="e1393-138">The remote party has signed the `hashValue` using the SHA1 algorithm, producing the digital signature `signedHashValue`.</span></span> <span data-ttu-id="e1393-139">Metoda <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> ověří, zda je digitální podpis platný a byl použit k podepsání `hashValue`.</span><span class="sxs-lookup"><span data-stu-id="e1393-139">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> method verifies that the digital signature is valid and was used to sign the `hashValue`.</span></span>

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

<span data-ttu-id="e1393-140">V tomto fragmentu kódu se zobrazí "`The signature is valid`", pokud je podpis platný a "`The signature is not valid`", pokud není.</span><span class="sxs-lookup"><span data-stu-id="e1393-140">This code fragment will display "`The signature is valid`" if the signature is valid and "`The signature is not valid`" if it is not.</span></span>

## <a name="see-also"></a><span data-ttu-id="e1393-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e1393-141">See also</span></span>

- [<span data-ttu-id="e1393-142">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="e1393-142">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
