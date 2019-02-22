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
ms.openlocfilehash: 314c8b7268549380143a608bb423f849ad0bb64c
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2019
ms.locfileid: "56583265"
---
# <a name="cryptographic-signatures"></a><span data-ttu-id="d08f8-102">Kryptografické podpisy</span><span class="sxs-lookup"><span data-stu-id="d08f8-102">Cryptographic Signatures</span></span>
<a name="top"></a> <span data-ttu-id="d08f8-103">Šifrování digitálních podpisů zajistit integritu dat použít algoritmy pro veřejné klíče.</span><span class="sxs-lookup"><span data-stu-id="d08f8-103">Cryptographic digital signatures use public key algorithms to provide data integrity.</span></span> <span data-ttu-id="d08f8-104">Při podpisu dat pomocí digitálního podpisu někomu jinému můžete ověřit podpis a můžete prokázat, že data pochází od vás a nebyl změněn po jste zaregistrovali.</span><span class="sxs-lookup"><span data-stu-id="d08f8-104">When you sign data with a digital signature, someone else can verify the signature, and can prove that the data originated from you and was not altered after you signed it.</span></span> <span data-ttu-id="d08f8-105">Další informace o digitálních podpisů najdete v tématu [šifrovacím službám](../../../docs/standard/security/cryptographic-services.md).</span><span class="sxs-lookup"><span data-stu-id="d08f8-105">For more information about digital signatures, see [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md).</span></span>  
  
 <span data-ttu-id="d08f8-106">Toto téma vysvětluje, jak vytvořit a ověřit pomocí tříd v digitální podpisy <xref:System.Security.Cryptography?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d08f8-106">This topic explains how to generate and verify digital signatures using classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>  
  
-   [<span data-ttu-id="d08f8-107">Generování podpisů</span><span class="sxs-lookup"><span data-stu-id="d08f8-107">Generating Signatures</span></span>](#generate)  
  
-   [<span data-ttu-id="d08f8-108">Ověření podpisů</span><span class="sxs-lookup"><span data-stu-id="d08f8-108">Verifying Signatures</span></span>](#verify)  
  
<a name="generate"></a>   
## <a name="generating-signatures"></a><span data-ttu-id="d08f8-109">Generování podpisů</span><span class="sxs-lookup"><span data-stu-id="d08f8-109">Generating Signatures</span></span>  
 <span data-ttu-id="d08f8-110">Digitální podpisy jsou obvykle použity na hodnoty hash, jež reprezentují data větší.</span><span class="sxs-lookup"><span data-stu-id="d08f8-110">Digital signatures are usually applied to hash values that represent larger data.</span></span> <span data-ttu-id="d08f8-111">Následující příklad se týká digitální podpis hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="d08f8-111">The following example applies a digital signature to a hash value.</span></span> <span data-ttu-id="d08f8-112">První, novou instanci třídy <xref:System.Security.Cryptography.RSACryptoServiceProvider> ke generování dvojice veřejného/soukromého klíče je vytvořená třída.</span><span class="sxs-lookup"><span data-stu-id="d08f8-112">First, a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class is created to generate a public/private key pair.</span></span> <span data-ttu-id="d08f8-113">Dále <xref:System.Security.Cryptography.RSACryptoServiceProvider> je předán do nové instance <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> třídy.</span><span class="sxs-lookup"><span data-stu-id="d08f8-113">Next, the <xref:System.Security.Cryptography.RSACryptoServiceProvider> is passed to a new instance of the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class.</span></span> <span data-ttu-id="d08f8-114">Toto převede privátní klíč, aby <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, která ve skutečnosti provádí digitální podpis.</span><span class="sxs-lookup"><span data-stu-id="d08f8-114">This transfers the private key to the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, which actually performs the digital signing.</span></span> <span data-ttu-id="d08f8-115">Předtím, než hodnota hash se můžete přihlásit, je nutné zadat hashovací algoritmus k použití.</span><span class="sxs-lookup"><span data-stu-id="d08f8-115">Before you can sign the hash code, you must specify a hash algorithm to use.</span></span> <span data-ttu-id="d08f8-116">Tento příklad používá algoritmus SHA1.</span><span class="sxs-lookup"><span data-stu-id="d08f8-116">This example uses the SHA1 algorithm.</span></span> <span data-ttu-id="d08f8-117">Nakonec <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> metoda je volána k provedení podpisu.</span><span class="sxs-lookup"><span data-stu-id="d08f8-117">Finally, the <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> method is called to perform the signing.</span></span>  
  
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
  
using System;  
using System.Security.Cryptography;  
```  
  
```csharp  
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
  
### <a name="signing-xml-files"></a><span data-ttu-id="d08f8-118">Podepisování souborů XML</span><span class="sxs-lookup"><span data-stu-id="d08f8-118">Signing XML Files</span></span>  
 <span data-ttu-id="d08f8-119">Rozhraní .NET Framework poskytuje <xref:System.Security.Cryptography.Xml> obor názvů, který vám umožní přihlásit XML.</span><span class="sxs-lookup"><span data-stu-id="d08f8-119">The .NET Framework provides the <xref:System.Security.Cryptography.Xml> namespace, which enables you sign XML.</span></span> <span data-ttu-id="d08f8-120">Podpis XML je důležité, pokud chcete ověřit, že kód XML pocházejí z určitého zdroje.</span><span class="sxs-lookup"><span data-stu-id="d08f8-120">Signing XML is important when you want to verify that the XML originates from a certain source.</span></span> <span data-ttu-id="d08f8-121">Například pokud používáte službu akcií, která používá XML, můžete ověřit zdroj dat XML, pokud je podepsáno.</span><span class="sxs-lookup"><span data-stu-id="d08f8-121">For example, if you are using a stock quote service that uses XML, you can verify the source of the XML if it is signed.</span></span>  
  
 <span data-ttu-id="d08f8-122">Postupujte podle třídy v tomto oboru názvů [syntaxe XML – podpis a doporučení zpracování](https://www.w3.org/TR/xmldsig-core/) z World Wide Web Consortium.</span><span class="sxs-lookup"><span data-stu-id="d08f8-122">The classes in this namespace follow the [XML-Signature Syntax and Processing recommendation](https://www.w3.org/TR/xmldsig-core/) from the World Wide Web Consortium.</span></span>  
  
 [<span data-ttu-id="d08f8-123">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="d08f8-123">Back to top</span></span>](#top)  
  
<a name="verify"></a>   
## <a name="verifying-signatures"></a><span data-ttu-id="d08f8-124">Ověření podpisů</span><span class="sxs-lookup"><span data-stu-id="d08f8-124">Verifying Signatures</span></span>  
 <span data-ttu-id="d08f8-125">Pokud chcete ověřit, že data byla podepsána konkrétní osobou, musíte mít následující informace:</span><span class="sxs-lookup"><span data-stu-id="d08f8-125">To verify that data was signed by a particular party, you must have the following information:</span></span>  
  
-   <span data-ttu-id="d08f8-126">Veřejný klíč ze strany, který podepsal data.</span><span class="sxs-lookup"><span data-stu-id="d08f8-126">The public key of the party that signed the data.</span></span>  
  
-   <span data-ttu-id="d08f8-127">Digitální podpis.</span><span class="sxs-lookup"><span data-stu-id="d08f8-127">The digital signature.</span></span>  
  
-   <span data-ttu-id="d08f8-128">Data, která byla podepsána.</span><span class="sxs-lookup"><span data-stu-id="d08f8-128">The data that was signed.</span></span>  
  
-   <span data-ttu-id="d08f8-129">Hashovací algoritmus používaný podpisu.</span><span class="sxs-lookup"><span data-stu-id="d08f8-129">The hash algorithm used by the signer.</span></span>  
  
 <span data-ttu-id="d08f8-130">Ověření podpisu podepsány <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> třídy, použijte <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> třídy.</span><span class="sxs-lookup"><span data-stu-id="d08f8-130">To verify a signature signed by the <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> class, use the <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class.</span></span> <span data-ttu-id="d08f8-131"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> Třída musí být zadaný veřejný klíč podpisu.</span><span class="sxs-lookup"><span data-stu-id="d08f8-131">The <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> class must be supplied the public key of the signer.</span></span> <span data-ttu-id="d08f8-132">Budete potřebovat hodnoty modulo a exponent zadat veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="d08f8-132">You will need the values of the modulus and the exponent to specify the public key.</span></span> <span data-ttu-id="d08f8-133">(Strany, který vygeneroval pár veřejného a privátního klíče by měla poskytnout tyto hodnoty.) Nejprve vytvořte <xref:System.Security.Cryptography.RSACryptoServiceProvider> objekt pro uložení veřejný klíč, který ověří podpis a následně inicializujete <xref:System.Security.Cryptography.RSAParameters> strukturu pro operace modulo a exponent hodnoty, které určují veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="d08f8-133">(The party that generated the public/private key pair should provide these values.) First create an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to hold the public key that will verify the signature, and then initialize an <xref:System.Security.Cryptography.RSAParameters> structure to the modulus and exponent values that specify the public key.</span></span>  
  
 <span data-ttu-id="d08f8-134">Následující kód ukazuje vytvoření objektu <xref:System.Security.Cryptography.RSAParameters> struktury.</span><span class="sxs-lookup"><span data-stu-id="d08f8-134">The following code shows the creation of an <xref:System.Security.Cryptography.RSAParameters> structure.</span></span> <span data-ttu-id="d08f8-135">`Modulus` Je nastavena na hodnotu pole bajtů s názvem `modulusData` a `Exponent` je nastavena na hodnotu pole bajtů s názvem `exponentData`.</span><span class="sxs-lookup"><span data-stu-id="d08f8-135">The `Modulus` property is set to the value of a byte array called `modulusData` and the `Exponent` property is set to the value of a byte array called `exponentData`.</span></span>  
  
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
  
 <span data-ttu-id="d08f8-136">Po vytvoření <xref:System.Security.Cryptography.RSAParameters> objektu, můžete inicializovat novou instanci třídy <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy hodnotám zadaným v <xref:System.Security.Cryptography.RSAParameters>.</span><span class="sxs-lookup"><span data-stu-id="d08f8-136">After you have created the <xref:System.Security.Cryptography.RSAParameters> object, you can initialize a new instance of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class to the values specified in <xref:System.Security.Cryptography.RSAParameters>.</span></span> <span data-ttu-id="d08f8-137"><xref:System.Security.Cryptography.RSACryptoServiceProvider> Je předán konstruktoru <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> pro přenos klíče.</span><span class="sxs-lookup"><span data-stu-id="d08f8-137">The <xref:System.Security.Cryptography.RSACryptoServiceProvider> is, in turn, passed to the constructor of an <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> to transfer the key.</span></span>  
  
 <span data-ttu-id="d08f8-138">Tento proces je znázorněn v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d08f8-138">The following example illustrates this process.</span></span> <span data-ttu-id="d08f8-139">V tomto příkladu `hashValue` a `signedHashValue` jsou pole bajtů poskytované Vzdálená strana.</span><span class="sxs-lookup"><span data-stu-id="d08f8-139">In this example, `hashValue` and `signedHashValue` are arrays of bytes provided by a remote party.</span></span> <span data-ttu-id="d08f8-140">Vzdálená strana podepsala `hashValue` použití algoritmů SHA1, vytváření digitálního podpisu `signedHashValue`.</span><span class="sxs-lookup"><span data-stu-id="d08f8-140">The remote party has signed the `hashValue` using the SHA1 algorithm, producing the digital signature `signedHashValue`.</span></span> <span data-ttu-id="d08f8-141">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="d08f8-141">The</span></span>  
  
 <span data-ttu-id="d08f8-142"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> Metoda ověří, že digitální podpis je platný a se použil k podepsání `hashValue`.</span><span class="sxs-lookup"><span data-stu-id="d08f8-142"><xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> method verifies that the digital signature is valid and was used to sign the `hashValue`.</span></span>  
  
```vb  
Dim rsa As New RSACryptoServiceProvider()  
rsa.ImportParameters(rsaKeyInfo)  
Dim rsaDeformatter As New RSAPKCS1SignatureDeformatter(rsa)  
rsaDeformatter.SetHashAlgorithm("SHA1")  
If rsaDeformatter.VerifySignature(hashValue, signedHashValue) Then  
   Console.WriteLine("The signature is valid.")  
Else  
   Console.WriteLine("The signture is not valid.")  
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
  
 <span data-ttu-id="d08f8-143">Tento fragment kódu se zobrazí "`The signature is valid`" Pokud podpis je platný a "`The signature is not valid`" Pokud není.</span><span class="sxs-lookup"><span data-stu-id="d08f8-143">This code fragment will display "`The signature is valid`" if the signature is valid and "`The signature is not valid`" if it is not.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d08f8-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d08f8-144">See also</span></span>

- [<span data-ttu-id="d08f8-145">Kryptografické služby</span><span class="sxs-lookup"><span data-stu-id="d08f8-145">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
