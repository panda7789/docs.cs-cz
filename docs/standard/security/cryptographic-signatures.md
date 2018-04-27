---
title: Kryptografické podpisy
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 17
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 596625f229c4031b681755d538bf0a3d7b6674c8
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="cryptographic-signatures"></a><span data-ttu-id="fa7d7-102">Kryptografické podpisy</span><span class="sxs-lookup"><span data-stu-id="fa7d7-102">Cryptographic Signatures</span></span>
<a name="top"></a> <span data-ttu-id="fa7d7-103">Kryptografické digitální podpisy zajistit integritu dat použít algoritmy s veřejným klíčem.</span><span class="sxs-lookup"><span data-stu-id="fa7d7-103">Cryptographic digital signatures use public key algorithms to provide data integrity.</span></span> <span data-ttu-id="fa7d7-104">Při podepisování dat pomocí digitálního podpisu někdo lze ověřit podpis a může prokázat, že data pochází od vás a nebyla změněna poté, co jste se přihlásili ho.</span><span class="sxs-lookup"><span data-stu-id="fa7d7-104">When you sign data with a digital signature, someone else can verify the signature, and can prove that the data originated from you and was not altered after you signed it.</span></span> <span data-ttu-id="fa7d7-105">Další informace o digitálních podpisů najdete v tématu [šifrovacím službám](../../../docs/standard/security/cryptographic-services.md).</span><span class="sxs-lookup"><span data-stu-id="fa7d7-105">For more information about digital signatures, see [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md).</span></span>  
  
 <span data-ttu-id="fa7d7-106">Toto téma vysvětluje, jak vytvořit a ověřit digitální podpisy pomocí tříd v <xref:System.Security.Cryptography?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="fa7d7-106">This topic explains how to generate and verify digital signatures using classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>  
  
-   [<span data-ttu-id="fa7d7-107">Generování podpisů</span><span class="sxs-lookup"><span data-stu-id="fa7d7-107">Generating Signatures</span></span>](#generate)  
  
-   [<span data-ttu-id="fa7d7-108">Ověření podpisů</span><span class="sxs-lookup"><span data-stu-id="fa7d7-108">Verifying Signatures</span></span>](#verify)  
  
<a name="generate"></a>   
## <a name="generating-signatures"></a><span data-ttu-id="fa7d7-109">Generování podpisů</span><span class="sxs-lookup"><span data-stu-id="fa7d7-109">Generating Signatures</span></span>  
 <span data-ttu-id="fa7d7-110">Digitální podpisy obvykle platí pro hodnoty hash, které představují větší data.</span><span class="sxs-lookup"><span data-stu-id="fa7d7-110">Digital signatures are usually applied to hash values that represent larger data.</span></span> <span data-ttu-id="fa7d7-111">Následující příklad se týká digitální podpis hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="fa7d7-111">The following example applies a digital signature to a hash value.</span></span> <span data-ttu-id="fa7d7-112">První, novou instanci třídy <xref:System.Security.Cryptography.RSACryptoServiceProvider> ke generování páru veřejného a privátního klíče RSA je vytvořit třídu.</span><span class="sxs-lookup"><span data-stu-id="fa7d7-112">First, a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class is created to generate a public/private key pair.</span></span> <span data-ttu-id="fa7d7-113">Dále <xref:System.Security.Cryptography.RSACryptoServiceProvider> předaný novou instanci třídy <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> třídy.</span><span class="sxs-lookup"><span data-stu-id="fa7d7-113">Next, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> is passed to a new instance of the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class.</span></span> <span data-ttu-id="fa7d7-114">Toto převede privátní klíč, aby <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, která ve skutečnosti provádí digitální podpis.</span><span class="sxs-lookup"><span data-stu-id="fa7d7-114">This transfers the private key to the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, which actually performs the digital signing.</span></span> <span data-ttu-id="fa7d7-115">Předtím, než hodnota hash se můžete přihlásit, musíte zadat algoritmus hash k použití.</span><span class="sxs-lookup"><span data-stu-id="fa7d7-115">Before you can sign the hash code, you must specify a hash algorithm to use.</span></span> <span data-ttu-id="fa7d7-116">Tento příklad používá algoritmus SHA1.</span><span class="sxs-lookup"><span data-stu-id="fa7d7-116">This example uses the SHA1 algorithm.</span></span> <span data-ttu-id="fa7d7-117">Nakonec <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> metoda je volána k provedení podpisu.</span><span class="sxs-lookup"><span data-stu-id="fa7d7-117">Finally, the <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> method is called to perform the signing.</span></span>  
  
```vb  
Imports System  
Imports System.Security.Cryptography  
  
Module Module1  
    Sub Main()  
        'The hash value to sign.  
        Dim HashValue As Byte() = {59, 4, 248, 102, 77, 97, 142, 201, 210, 12, 224, 93, 25, 41, 100, 197, 213, 134, 130, 135}  
  
        'The value to hold the signed value.  
        Dim SignedHashValue() As Byte  
  
        'Generate a public/private key pair.  
        Dim RSA As New RSACryptoServiceProvider()  
  
        'Create an RSAPKCS1SignatureFormatter object and pass it   
        'the RSACryptoServiceProvider to transfer the private key.  
        Dim RSAFormatter As New RSAPKCS1SignatureFormatter(RSA)  
  
        'Set the hash algorithm to SHA1.  
        RSAFormatter.SetHashAlgorithm("SHA1")  
  
        'Create a signature for HashValue and assign it to   
        'SignedHashValue.  
        SignedHashValue = RSAFormatter.CreateSignature(HashValue)  
    End Sub  
End Module  
  
using System;  
using System.Security.Cryptography;  
```  
  
```csharp  
class Class1  
{  
   static void Main()  
   {  
      //The hash value to sign.  
      byte[] HashValue = {59,4,248,102,77,97,142,201,210,12,224,93,25,41,100,197,213,134,130,135};  
  
      //The value to hold the signed value.  
      byte[] SignedHashValue;  
  
      //Generate a public/private key pair.  
      RSACryptoServiceProvider RSA = new RSACryptoServiceProvider();  
  
      //Create an RSAPKCS1SignatureFormatter object and pass it the   
      //RSACryptoServiceProvider to transfer the private key.  
      RSAPKCS1SignatureFormatter RSAFormatter = new RSAPKCS1SignatureFormatter(RSA);  
  
      //Set the hash algorithm to SHA1.  
      RSAFormatter.SetHashAlgorithm("SHA1");  
  
      //Create a signature for HashValue and assign it to   
      //SignedHashValue.  
      SignedHashValue = RSAFormatter.CreateSignature(HashValue);  
   }  
}  
```  
  
### <a name="signing-xml-files"></a><span data-ttu-id="fa7d7-118">Podpis souborů XML</span><span class="sxs-lookup"><span data-stu-id="fa7d7-118">Signing XML Files</span></span>  
 <span data-ttu-id="fa7d7-119">Poskytuje rozhraní .NET Framework <xref:System.Security.Cryptography.Xml> názvů, což vám umožní přihlásit XML.</span><span class="sxs-lookup"><span data-stu-id="fa7d7-119">The .NET Framework provides the <xref:System.Security.Cryptography.Xml> namespace, which enables you sign XML.</span></span> <span data-ttu-id="fa7d7-120">Podpis XML je důležité, pokud chcete ověřit, že soubor XML pocházejí z určitého zdroje.</span><span class="sxs-lookup"><span data-stu-id="fa7d7-120">Signing XML is important when you want to verify that the XML originates from a certain source.</span></span> <span data-ttu-id="fa7d7-121">Například pokud používáte služby akcií, který se používá soubor XML, můžete ověřit zdroj XML je podepsaný.</span><span class="sxs-lookup"><span data-stu-id="fa7d7-121">For example, if you are using a stock quote service that uses XML, you can verify the source of the XML if it is signed.</span></span>  
  
 <span data-ttu-id="fa7d7-122">Postupujte podle třídy v tomto oboru názvů [syntaxe podpisu XML a doporučení zpracování](https://www.w3.org/TR/xmldsig-core/) z World Wide Web Consortium.</span><span class="sxs-lookup"><span data-stu-id="fa7d7-122">The classes in this namespace follow the [XML-Signature Syntax and Processing recommendation](https://www.w3.org/TR/xmldsig-core/) from the World Wide Web Consortium.</span></span>  
  
 [<span data-ttu-id="fa7d7-123">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="fa7d7-123">Back to top</span></span>](#top)  
  
<a name="verify"></a>   
## <a name="verifying-signatures"></a><span data-ttu-id="fa7d7-124">Ověření podpisů</span><span class="sxs-lookup"><span data-stu-id="fa7d7-124">Verifying Signatures</span></span>  
 <span data-ttu-id="fa7d7-125">Pokud chcete ověřit, že data byla podepsána konkrétní osobou, musíte mít následující informace:</span><span class="sxs-lookup"><span data-stu-id="fa7d7-125">To verify that data was signed by a particular party, you must have the following information:</span></span>  
  
-   <span data-ttu-id="fa7d7-126">Veřejný klíč stranu, která je podepsaná data.</span><span class="sxs-lookup"><span data-stu-id="fa7d7-126">The public key of the party that signed the data.</span></span>  
  
-   <span data-ttu-id="fa7d7-127">Digitální podpis.</span><span class="sxs-lookup"><span data-stu-id="fa7d7-127">The digital signature.</span></span>  
  
-   <span data-ttu-id="fa7d7-128">Data, která je podepsaná.</span><span class="sxs-lookup"><span data-stu-id="fa7d7-128">The data that was signed.</span></span>  
  
-   <span data-ttu-id="fa7d7-129">Algoritmu hash používaného podepisující osoba.</span><span class="sxs-lookup"><span data-stu-id="fa7d7-129">The hash algorithm used by the signer.</span></span>  
  
 <span data-ttu-id="fa7d7-130">K ověření podpisu podepsaný <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> třídy, použijte <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> třídy.</span><span class="sxs-lookup"><span data-stu-id="fa7d7-130">To verify a signature signed by the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class, use the <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class.</span></span> <span data-ttu-id="fa7d7-131"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> Třída musí být zadán veřejný klíč autora podpisu.</span><span class="sxs-lookup"><span data-stu-id="fa7d7-131">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class must be supplied the public key of the signer.</span></span> <span data-ttu-id="fa7d7-132">Budete potřebovat hodnoty zbytku a exponent zadat veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="fa7d7-132">You will need the values of the modulus and the exponent to specify the public key.</span></span> <span data-ttu-id="fa7d7-133">(Stranu, která generuje pár veřejného a privátního klíče by měl poskytovat tyto hodnoty.) Nejprve vytvořit <xref:System.Security.Cryptography.RSACryptoServiceProvider> objekt pro uložení veřejný klíč, který ověří podpis a potom inicializujte <xref:System.Security.Cryptography.RSAParameters> struktura na numerického zbytku a exponent hodnoty, které určují veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="fa7d7-133">(The party that generated the public/private key pair should provide these values.) First create an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to hold the public key that will verify the signature, and then initialize an <xref:System.Security.Cryptography.RSAParameters> structure to the modulus and exponent values that specify the public key.</span></span>  
  
 <span data-ttu-id="fa7d7-134">Následující kód ukazuje vytvoření <xref:System.Security.Cryptography.RSAParameters> struktura.</span><span class="sxs-lookup"><span data-stu-id="fa7d7-134">The following code shows the creation of an <xref:System.Security.Cryptography.RSAParameters> structure.</span></span> <span data-ttu-id="fa7d7-135">`Modulus` Je nastavena na hodnotu bajtové pole nazvané `ModulusData` a `Exponent` je nastavena na hodnotu bajtové pole nazvané `ExponentData`.</span><span class="sxs-lookup"><span data-stu-id="fa7d7-135">The `Modulus` property is set to the value of a byte array called `ModulusData` and the `Exponent` property is set to the value of a byte array called `ExponentData`.</span></span>  
  
```vb  
Dim RSAKeyInfo As RSAParameters  
RSAKeyInfo.Modulus = ModulusData  
RSAKeyInfo.Exponent = ExponentData  
```  
  
```csharp  
RSAParameters RSAKeyInfo;  
RSAKeyInfo.Modulus = ModulusData;  
RSAKeyInfo.Exponent = ExponentData;  
```  
  
 <span data-ttu-id="fa7d7-136">Po vytvoření <xref:System.Security.Cryptography.RSAParameters> objektu, bude možné inicializovat novou instanci třídy <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy hodnoty zadané v <xref:System.Security.Cryptography.RSAParameters>.</span><span class="sxs-lookup"><span data-stu-id="fa7d7-136">After you have created the <xref:System.Security.Cryptography.RSAParameters> object, you can initialize a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class to the values specified in <xref:System.Security.Cryptography.RSAParameters>.</span></span> <span data-ttu-id="fa7d7-137"><xref:System.Security.Cryptography.RSACryptoServiceProvider> Se naopak předaný do konstruktoru objektu <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> pro přenos klíče.</span><span class="sxs-lookup"><span data-stu-id="fa7d7-137">The <xref:System.Security.Cryptography.RSACryptoServiceProvider> is, in turn, passed to the constructor of an <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> to transfer the key.</span></span>  
  
 <span data-ttu-id="fa7d7-138">Tento proces je znázorněn v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="fa7d7-138">The following example illustrates this process.</span></span> <span data-ttu-id="fa7d7-139">V tomto příkladu `HashValue` a `SignedHashValue` jsou pole bajtů poskytované vzdálené strany.</span><span class="sxs-lookup"><span data-stu-id="fa7d7-139">In this example, `HashValue` and `SignedHashValue` are arrays of bytes provided by a remote party.</span></span> <span data-ttu-id="fa7d7-140">Vzdálené strany podepsala `HashValue` pomocí algoritmu SHA1, který vytvořil digitální podpis `SignedHashValue`.</span><span class="sxs-lookup"><span data-stu-id="fa7d7-140">The remote party has signed the `HashValue` using the SHA1 algorithm, producing the digital signature `SignedHashValue`.</span></span> <span data-ttu-id="fa7d7-141">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="fa7d7-141">The</span></span>  
  
 <span data-ttu-id="fa7d7-142"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> Metoda ověří, že je platný digitální podpis a se použil k podepsání `HashValue`.</span><span class="sxs-lookup"><span data-stu-id="fa7d7-142"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> method verifies that the digital signature is valid and was used to sign the `HashValue`.</span></span>  
  
```vb  
Dim RSA As New RSACryptoServiceProvider()  
RSA.ImportParameters(RSAKeyInfo)  
Dim RSADeformatter As New RSAPKCS1SignatureDeformatter(RSA)  
RSADeformatter.SetHashAlgorithm("SHA1")  
If RSADeformatter.VerifySignature(HashValue, SignedHashValue) Then  
   Console.WriteLine("The signature is valid.")  
Else  
   Console.WriteLine("The signture is not valid.")  
End If  
```  
  
```csharp  
RSACryptoServiceProvider RSA = new RSACryptoServiceProvider();  
RSA.ImportParameters(RSAKeyInfo);  
RSAPKCS1SignatureDeformatter RSADeformatter = new RSAPKCS1SignatureDeformatter(RSA);  
RSADeformatter.SetHashAlgorithm("SHA1");  
if(RSADeformatter.VerifySignature(HashValue, SignedHashValue))  
{  
   Console.WriteLine("The signature is valid.");  
}  
else  
{  
   Console.WriteLine("The signature is not valid.");  
}  
```  
  
 <span data-ttu-id="fa7d7-143">Tento fragment kódu zobrazí "`The signature is valid`" Pokud podpis je neplatný a "`The signature is not valid`" Pokud není.</span><span class="sxs-lookup"><span data-stu-id="fa7d7-143">This code fragment will display "`The signature is valid`" if the signature is valid and "`The signature is not valid`" if it is not.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa7d7-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="fa7d7-144">See Also</span></span>  
 [<span data-ttu-id="fa7d7-145">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="fa7d7-145">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
