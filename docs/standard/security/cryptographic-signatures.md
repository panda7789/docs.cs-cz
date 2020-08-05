---
title: Kryptografické podpisy
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- digital signatures
- cryptography [.NET], signatures
- digital signatures, XML signing
- signatures, cryptographic
- digital signatures, generating
- verifying signatures
- generating signatures
- digital signatures, about
- encryption [.NET], signatures
- security [.NET], signatures
- XML signing
- digital signatures, verifying
- signing XML
ms.assetid: aa87cb7f-e608-4a81-948b-c9b8a1225783
ms.openlocfilehash: ce2be1d509da4e399bf87e1c8df7ba061fc2707c
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557005"
---
# <a name="cryptographic-signatures"></a><span data-ttu-id="be95d-102">Kryptografické podpisy</span><span class="sxs-lookup"><span data-stu-id="be95d-102">Cryptographic Signatures</span></span>

<span data-ttu-id="be95d-103">Kryptografické digitální podpisy využívají algoritmy veřejného klíče k zajištění integrity dat.</span><span class="sxs-lookup"><span data-stu-id="be95d-103">Cryptographic digital signatures use public key algorithms to provide data integrity.</span></span> <span data-ttu-id="be95d-104">Když podepisujete data digitálním podpisem, někdo jiný může podpis ověřit a může prokázat, že data pocházejí z vás a že se po jejím podepsání nezměnila.</span><span class="sxs-lookup"><span data-stu-id="be95d-104">When you sign data with a digital signature, someone else can verify the signature, and can prove that the data originated from you and was not altered after you signed it.</span></span> <span data-ttu-id="be95d-105">Další informace o digitálních podpisech najdete v tématu [kryptografické služby](cryptographic-services.md).</span><span class="sxs-lookup"><span data-stu-id="be95d-105">For more information about digital signatures, see [Cryptographic Services](cryptographic-services.md).</span></span>

<span data-ttu-id="be95d-106">Toto téma vysvětluje, jak vygenerovat a ověřit digitální podpisy pomocí tříd v <xref:System.Security.Cryptography> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="be95d-106">This topic explains how to generate and verify digital signatures using classes in the <xref:System.Security.Cryptography> namespace.</span></span>

## <a name="generating-signatures"></a><span data-ttu-id="be95d-107">Generování podpisů</span><span class="sxs-lookup"><span data-stu-id="be95d-107">Generating Signatures</span></span>

<span data-ttu-id="be95d-108">Digitální podpisy jsou obvykle aplikovány na hodnoty hash, které představují větší data.</span><span class="sxs-lookup"><span data-stu-id="be95d-108">Digital signatures are usually applied to hash values that represent larger data.</span></span> <span data-ttu-id="be95d-109">Následující příklad aplikuje digitální podpis na hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="be95d-109">The following example applies a digital signature to a hash value.</span></span> <span data-ttu-id="be95d-110">Nejprve se vytvoří nová instance třídy, <xref:System.Security.Cryptography.RSA> která vygeneruje pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="be95d-110">First, a new instance of the <xref:System.Security.Cryptography.RSA> class is created to generate a public/private key pair.</span></span> <span data-ttu-id="be95d-111">Dále <xref:System.Security.Cryptography.RSA> je předána do nové instance <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> třídy.</span><span class="sxs-lookup"><span data-stu-id="be95d-111">Next, the <xref:System.Security.Cryptography.RSA> is passed to a new instance of the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class.</span></span> <span data-ttu-id="be95d-112">Tím se privátní klíč přenáší do <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> , který skutečně provádí digitální podepisování.</span><span class="sxs-lookup"><span data-stu-id="be95d-112">This transfers the private key to the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, which actually performs the digital signing.</span></span> <span data-ttu-id="be95d-113">Než budete moci podepsat kód hash, je nutné zadat algoritmus hash, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="be95d-113">Before you can sign the hash code, you must specify a hash algorithm to use.</span></span> <span data-ttu-id="be95d-114">V tomto příkladu se používá algoritmus SHA1.</span><span class="sxs-lookup"><span data-stu-id="be95d-114">This example uses the SHA1 algorithm.</span></span> <span data-ttu-id="be95d-115">Nakonec <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> je volána metoda pro provedení podepisování.</span><span class="sxs-lookup"><span data-stu-id="be95d-115">Finally, the <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> method is called to perform the signing.</span></span>

<span data-ttu-id="be95d-116">Z důvodu kolizí problémů se SHA1 doporučujeme SHA256 nebo lepší.</span><span class="sxs-lookup"><span data-stu-id="be95d-116">Due to collision problems with SHA1, we recommend SHA256 or better.</span></span>

```vb
Imports System.Security.Cryptography

Module Module1
    Sub Main()
        'The hash value to sign.
        Dim hashValue As Byte() = {59, 4, 248, 102, 77, 97, 142, 201, 210, 12, 224, 93, 25, 41, 100, 197, 213, 134, 130, 135}

        'The value to hold the signed value.
        Dim signedHashValue() As Byte

        'Generate a public/private key pair.
        Dim rsa As RSA = RSA.Create()

        'Create an RSAPKCS1SignatureFormatter object and pass it
        'the RSA instance to transfer the private key.
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
      RSA rsa = RSA.Create();

      //Create an RSAPKCS1SignatureFormatter object and pass it the
      //RSA instance to transfer the private key.
      RSAPKCS1SignatureFormatter rsaFormatter = new RSAPKCS1SignatureFormatter(rsa);

      //Set the hash algorithm to SHA1.
      rsaFormatter.SetHashAlgorithm("SHA1");

      //Create a signature for hashValue and assign it to
      //signedHashValue.
      signedHashValue = rsaFormatter.CreateSignature(hashValue);
   }
}
```

## <a name="verifying-signatures"></a><span data-ttu-id="be95d-117">Ověřování podpisů</span><span class="sxs-lookup"><span data-stu-id="be95d-117">Verifying Signatures</span></span>

<span data-ttu-id="be95d-118">Chcete-li ověřit, zda byla data podepsána konkrétní stranou, je nutné mít následující informace:</span><span class="sxs-lookup"><span data-stu-id="be95d-118">To verify that data was signed by a particular party, you must have the following information:</span></span>

- <span data-ttu-id="be95d-119">Veřejný klíč strany, která podepsala data.</span><span class="sxs-lookup"><span data-stu-id="be95d-119">The public key of the party that signed the data.</span></span>

- <span data-ttu-id="be95d-120">Digitální podpis.</span><span class="sxs-lookup"><span data-stu-id="be95d-120">The digital signature.</span></span>

- <span data-ttu-id="be95d-121">Data, která byla podepsána.</span><span class="sxs-lookup"><span data-stu-id="be95d-121">The data that was signed.</span></span>

- <span data-ttu-id="be95d-122">Algoritmus hash používaný podepsáním.</span><span class="sxs-lookup"><span data-stu-id="be95d-122">The hash algorithm used by the signer.</span></span>

<span data-ttu-id="be95d-123">Chcete-li ověřit podpis podepsaný <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> třídou, použijte <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> třídu.</span><span class="sxs-lookup"><span data-stu-id="be95d-123">To verify a signature signed by the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class, use the <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class.</span></span> <span data-ttu-id="be95d-124"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter>Třídě musí být dodán veřejný klíč podepsaného.</span><span class="sxs-lookup"><span data-stu-id="be95d-124">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class must be supplied the public key of the signer.</span></span> <span data-ttu-id="be95d-125">Pro RSA budete potřebovat hodnoty zbytku a exponentu k určení veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="be95d-125">For RSA, you will need the values of the modulus and the exponent to specify the public key.</span></span> <span data-ttu-id="be95d-126">(Strana, která vygenerovala pár veřejného a privátního klíče, by měla poskytnout tyto hodnoty.) Nejprve vytvořte <xref:System.Security.Cryptography.RSA> objekt, který bude obsahovat veřejný klíč, který ověří podpis, a poté inicializuje <xref:System.Security.Cryptography.RSAParameters> strukturu na hodnoty modulu a exponentu, které určují veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="be95d-126">(The party that generated the public/private key pair should provide these values.) First create an <xref:System.Security.Cryptography.RSA> object to hold the public key that will verify the signature, and then initialize an <xref:System.Security.Cryptography.RSAParameters> structure to the modulus and exponent values that specify the public key.</span></span>

<span data-ttu-id="be95d-127">Následující kód ukazuje vytvoření <xref:System.Security.Cryptography.RSAParameters> struktury.</span><span class="sxs-lookup"><span data-stu-id="be95d-127">The following code shows the creation of an <xref:System.Security.Cryptography.RSAParameters> structure.</span></span> <span data-ttu-id="be95d-128">`Modulus`Vlastnost je nastavena na hodnotu s názvem bajtového pole `modulusData` a `Exponent` vlastnost je nastavena na hodnotu s názvem bajtového pole `exponentData` .</span><span class="sxs-lookup"><span data-stu-id="be95d-128">The `Modulus` property is set to the value of a byte array called `modulusData` and the `Exponent` property is set to the value of a byte array called `exponentData`.</span></span>

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

<span data-ttu-id="be95d-129">Po vytvoření <xref:System.Security.Cryptography.RSAParameters> objektu můžete inicializovat novou instanci <xref:System.Security.Cryptography.RSA> implementační třídy na hodnoty, které jsou zadány v <xref:System.Security.Cryptography.RSAParameters> .</span><span class="sxs-lookup"><span data-stu-id="be95d-129">After you have created the <xref:System.Security.Cryptography.RSAParameters> object, you can initialize a new instance of the <xref:System.Security.Cryptography.RSA> implementation class to the values specified in <xref:System.Security.Cryptography.RSAParameters>.</span></span> <span data-ttu-id="be95d-130"><xref:System.Security.Cryptography.RSA>Instance je zase předána konstruktoru <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> pro přenos klíče.</span><span class="sxs-lookup"><span data-stu-id="be95d-130">The <xref:System.Security.Cryptography.RSA> instance is, in turn, passed to the constructor of an <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> to transfer the key.</span></span>

<span data-ttu-id="be95d-131">Následující příklad znázorňuje tento proces.</span><span class="sxs-lookup"><span data-stu-id="be95d-131">The following example illustrates this process.</span></span> <span data-ttu-id="be95d-132">V tomto příkladu `hashValue` `signedHashValue` jsou pole bajtů poskytnuté vzdálenou stranou.</span><span class="sxs-lookup"><span data-stu-id="be95d-132">In this example, `hashValue` and `signedHashValue` are arrays of bytes provided by a remote party.</span></span> <span data-ttu-id="be95d-133">Vzdálená strana podepsala certifikát `hashValue` pomocí algoritmu SHA1 a vytvořil digitální podpis `signedHashValue` .</span><span class="sxs-lookup"><span data-stu-id="be95d-133">The remote party has signed the `hashValue` using the SHA1 algorithm, producing the digital signature `signedHashValue`.</span></span> <span data-ttu-id="be95d-134"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType>Metoda ověřuje, zda je digitální podpis platný a byl použit k podepsání `hashValue` .</span><span class="sxs-lookup"><span data-stu-id="be95d-134">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> method verifies that the digital signature is valid and was used to sign the `hashValue`.</span></span>

<span data-ttu-id="be95d-135">Z důvodu kolizí problémů se SHA1 doporučujeme SHA256 nebo lepší.</span><span class="sxs-lookup"><span data-stu-id="be95d-135">Due to collision problems with SHA1, we recommend SHA256 or better.</span></span>  <span data-ttu-id="be95d-136">Pokud se ale pomocí algoritmu SHA1 vytvořil podpis, musíte k ověření podpisu použít SHA1.</span><span class="sxs-lookup"><span data-stu-id="be95d-136">However, if SHA1 was used to create the signature, you have to use SHA1 to verify the signature.</span></span>

```vb
Dim rsa As RSA = RSA.Create()
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
RSA rsa = RSA.Create();
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

<span data-ttu-id="be95d-137">Tento fragment kódu zobrazí " `The signature is valid` ", pokud je podpis platný a " `The signature is not valid` ", pokud není.</span><span class="sxs-lookup"><span data-stu-id="be95d-137">This code fragment will display "`The signature is valid`" if the signature is valid and "`The signature is not valid`" if it is not.</span></span>

## <a name="see-also"></a><span data-ttu-id="be95d-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="be95d-138">See also</span></span>

- [<span data-ttu-id="be95d-139">Šifrovací služby</span><span class="sxs-lookup"><span data-stu-id="be95d-139">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="be95d-140">Kryptografický model</span><span class="sxs-lookup"><span data-stu-id="be95d-140">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="be95d-141">Kryptografie pro různé platformy</span><span class="sxs-lookup"><span data-stu-id="be95d-141">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="be95d-142">Ochrana dat ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="be95d-142">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
