---
title: "Kryptografické podpisy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
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
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0651ae0fbc85b01d3e02354c06a9796804c8516e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="cryptographic-signatures"></a>Kryptografické podpisy
<a name="top"></a>Kryptografické digitální podpisy zajistit integritu dat použít algoritmy s veřejným klíčem. Při podepisování dat pomocí digitálního podpisu někdo lze ověřit podpis a může prokázat, že data pochází od vás a nebyla změněna poté, co jste se přihlásili ho. Další informace o digitálních podpisů najdete v tématu [šifrovacím službám](../../../docs/standard/security/cryptographic-services.md).  
  
 Toto téma vysvětluje, jak vytvořit a ověřit digitální podpisy pomocí tříd v <xref:System.Security.Cryptography?displayProperty=nameWithType> oboru názvů.  
  
-   [Generování podpisů](#generate)  
  
-   [Ověření podpisů](#verify)  
  
<a name="generate"></a>   
## <a name="generating-signatures"></a>Generování podpisů  
 Digitální podpisy obvykle platí pro hodnoty hash, které představují větší data. Následující příklad se týká digitální podpis hodnotu hash. První, novou instanci třídy <xref:System.Security.Cryptography.RSACryptoServiceProvider> ke generování páru veřejného a privátního klíče RSA je vytvořit třídu. Dále <xref:System.Security.Cryptography.RSACryptoServiceProvider> předaný novou instanci třídy <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> třídy. Toto převede privátní klíč, aby <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter>, která ve skutečnosti provádí digitální podpis. Předtím, než hodnota hash se můžete přihlásit, musíte zadat algoritmus hash k použití. Tento příklad používá algoritmus SHA1. Nakonec <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> metoda je volána k provedení podpisu.  
  
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
  
### <a name="signing-xml-files"></a>Podpis souborů XML  
 Poskytuje rozhraní .NET Framework <xref:System.Security.Cryptography.Xml> názvů, což vám umožní přihlásit XML. Podpis XML je důležité, pokud chcete ověřit, že soubor XML pocházejí z určitého zdroje. Například pokud používáte služby akcií, který se používá soubor XML, můžete ověřit zdroj XML je podepsaný.  
  
 Postupujte podle třídy v tomto oboru názvů [syntaxe podpisu XML a doporučení zpracování](http://go.microsoft.com/fwlink/?LinkId=136777) z World Wide Web Consortium.  
  
 [Zpět na začátek](#top)  
  
<a name="verify"></a>   
## <a name="verifying-signatures"></a>Ověření podpisů  
 Pokud chcete ověřit, že data byla podepsána konkrétní osobou, musíte mít následující informace:  
  
-   Veřejný klíč stranu, která je podepsaná data.  
  
-   Digitální podpis.  
  
-   Data, která je podepsaná.  
  
-   Algoritmu hash používaného podepisující osoba.  
  
 K ověření podpisu podepsaný <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> třídy, použijte <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> třídy. <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> Třída musí být zadán veřejný klíč autora podpisu. Budete potřebovat hodnoty zbytku a exponent zadat veřejný klíč. (Stranu, která generuje pár veřejného a privátního klíče by měl poskytovat tyto hodnoty.) Nejprve vytvořit <xref:System.Security.Cryptography.RSACryptoServiceProvider> objekt pro uložení veřejný klíč, který ověří podpis a potom inicializujte <xref:System.Security.Cryptography.RSAParameters> struktura na numerického zbytku a exponent hodnoty, které určují veřejný klíč.  
  
 Následující kód ukazuje vytvoření <xref:System.Security.Cryptography.RSAParameters> struktura. `Modulus` Je nastavena na hodnotu bajtové pole nazvané `ModulusData` a `Exponent` je nastavena na hodnotu bajtové pole nazvané `ExponentData`.  
  
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
  
 Po vytvoření <xref:System.Security.Cryptography.RSAParameters> objektu, bude možné inicializovat novou instanci třídy <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy hodnoty zadané v <xref:System.Security.Cryptography.RSAParameters>. <xref:System.Security.Cryptography.RSACryptoServiceProvider> Se naopak předaný do konstruktoru objektu <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> pro přenos klíče.  
  
 Tento proces je znázorněn v následujícím příkladu. V tomto příkladu `HashValue` a `SignedHashValue` jsou pole bajtů poskytované vzdálené strany. Vzdálené strany podepsala `HashValue` pomocí algoritmu SHA1, který vytvořil digitální podpis `SignedHashValue`. Rozhraní  
  
 <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType>Metoda ověří, že je platný digitální podpis a se použil k podepsání `HashValue`.  
  
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
  
 Tento fragment kódu zobrazí "`The signature is valid`" Pokud podpis je neplatný a "`The signature is not valid`" Pokud není.  
  
## <a name="see-also"></a>Viz také  
 [Kryptografické služby](../../../docs/standard/security/cryptographic-services.md)
