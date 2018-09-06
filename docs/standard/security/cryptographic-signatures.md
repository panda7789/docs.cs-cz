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
ms.openlocfilehash: 3f9d83a0edb6dc2261931e422b0ae4c735d2e0d1
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43869990"
---
# <a name="cryptographic-signatures"></a>Kryptografické podpisy
<a name="top"></a> Šifrování digitálních podpisů zajistit integritu dat použít algoritmy pro veřejné klíče. Při podpisu dat pomocí digitálního podpisu někomu jinému můžete ověřit podpis a můžete prokázat, že data pochází od vás a nebyl změněn po jste zaregistrovali. Další informace o digitálních podpisů najdete v tématu [šifrovacím službám](../../../docs/standard/security/cryptographic-services.md).  
  
 Toto téma vysvětluje, jak vytvořit a ověřit pomocí tříd v digitální podpisy <xref:System.Security.Cryptography?displayProperty=nameWithType> oboru názvů.  
  
-   [Generování podpisů](#generate)  
  
-   [Ověření podpisů](#verify)  
  
<a name="generate"></a>   
## <a name="generating-signatures"></a>Generování podpisů  
 Digitální podpisy jsou obvykle použity na hodnoty hash, jež reprezentují data větší. Následující příklad se týká digitální podpis hodnotu hash. První, novou instanci třídy <xref:System.Security.Cryptography.RSACryptoServiceProvider> ke generování dvojice veřejného/soukromého klíče je vytvořená třída. Dále <xref:System.Security.Cryptography.RSACryptoServiceProvider> je předán do nové instance <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> třídy. Toto převede privátní klíč, aby <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, která ve skutečnosti provádí digitální podpis. Předtím, než hodnota hash se můžete přihlásit, je nutné zadat hashovací algoritmus k použití. Tento příklad používá algoritmus SHA1. Nakonec <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> metoda je volána k provedení podpisu.  
  
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
  
### <a name="signing-xml-files"></a>Podepisování souborů XML  
 Rozhraní .NET Framework poskytuje <xref:System.Security.Cryptography.Xml> obor názvů, který vám umožní přihlásit XML. Podpis XML je důležité, pokud chcete ověřit, že kód XML pocházejí z určitého zdroje. Například pokud používáte službu akcií, která používá XML, můžete ověřit zdroj dat XML, pokud je podepsáno.  
  
 Postupujte podle třídy v tomto oboru názvů [syntaxe XML – podpis a doporučení zpracování](https://www.w3.org/TR/xmldsig-core/) z World Wide Web Consortium.  
  
 [Zpět na začátek](#top)  
  
<a name="verify"></a>   
## <a name="verifying-signatures"></a>Ověření podpisů  
 Pokud chcete ověřit, že data byla podepsána konkrétní osobou, musíte mít následující informace:  
  
-   Veřejný klíč ze strany, který podepsal data.  
  
-   Digitální podpis.  
  
-   Data, která byla podepsána.  
  
-   Hashovací algoritmus používaný podpisu.  
  
 Ověření podpisu podepsány <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> třídy, použijte <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> třídy. <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> Třída musí být zadaný veřejný klíč podpisu. Budete potřebovat hodnoty modulo a exponent zadat veřejný klíč. (Strany, který vygeneroval pár veřejného a privátního klíče by měla poskytnout tyto hodnoty.) Nejprve vytvořte <xref:System.Security.Cryptography.RSACryptoServiceProvider> objekt pro uložení veřejný klíč, který ověří podpis a následně inicializujete <xref:System.Security.Cryptography.RSAParameters> strukturu pro operace modulo a exponent hodnoty, které určují veřejný klíč.  
  
 Následující kód ukazuje vytvoření objektu <xref:System.Security.Cryptography.RSAParameters> struktury. `Modulus` Je nastavena na hodnotu pole bajtů s názvem `ModulusData` a `Exponent` je nastavena na hodnotu pole bajtů s názvem `ExponentData`.  
  
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
  
 Po vytvoření <xref:System.Security.Cryptography.RSAParameters> objektu, můžete inicializovat novou instanci třídy <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy hodnotám zadaným v <xref:System.Security.Cryptography.RSAParameters>. <xref:System.Security.Cryptography.RSACryptoServiceProvider> Je předán konstruktoru <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> pro přenos klíče.  
  
 Tento proces je znázorněn v následujícím příkladu. V tomto příkladu `HashValue` a `SignedHashValue` jsou pole bajtů poskytované Vzdálená strana. Vzdálená strana podepsala `HashValue` použití algoritmů SHA1, vytváření digitálního podpisu `SignedHashValue`. Rozhraní  
  
 <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType> Metoda ověří, že digitální podpis je platný a se použil k podepsání `HashValue`.  
  
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
  
 Tento fragment kódu se zobrazí "`The signature is valid`" Pokud podpis je platný a "`The signature is not valid`" Pokud není.  
  
## <a name="see-also"></a>Viz také:

- [Kryptografické služby](../../../docs/standard/security/cryptographic-services.md)
