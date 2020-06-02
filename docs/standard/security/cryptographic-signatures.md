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
ms.openlocfilehash: 9e69578ceffeeacb73cf059f5b577fe7c137b599
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288391"
---
# <a name="cryptographic-signatures"></a>Kryptografické podpisy

Kryptografické digitální podpisy využívají algoritmy veřejného klíče k zajištění integrity dat. Když podepisujete data digitálním podpisem, někdo jiný může podpis ověřit a může prokázat, že data pocházejí z vás a že se po jejím podepsání nezměnila. Další informace o digitálních podpisech najdete v tématu [kryptografické služby](cryptographic-services.md).

Toto téma vysvětluje, jak vygenerovat a ověřit digitální podpisy pomocí tříd v <xref:System.Security.Cryptography?displayProperty=nameWithType> oboru názvů.

## <a name="generating-signatures"></a>Generování podpisů

Digitální podpisy jsou obvykle aplikovány na hodnoty hash, které představují větší data. Následující příklad aplikuje digitální podpis na hodnotu hash. Nejprve se vytvoří nová instance třídy, <xref:System.Security.Cryptography.RSACryptoServiceProvider> která vygeneruje pár veřejného a privátního klíče. Dále <xref:System.Security.Cryptography.RSACryptoServiceProvider> je předána do nové instance <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> třídy. Tím se privátní klíč přenáší do <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> , který skutečně provádí digitální podepisování. Než budete moci podepsat kód hash, je nutné zadat algoritmus hash, který se má použít. V tomto příkladu se používá algoritmus SHA1. Nakonec <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> je volána metoda pro provedení podepisování.

Microsoft doporučuje SHA256 nebo lepší kvůli kolizi problémů se SHA1.

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

### <a name="signing-xml-files"></a>Podepisování souborů XML

.NET Framework poskytuje <xref:System.Security.Cryptography.Xml> obor názvů, který umožňuje podepisování XML. Podepisování XML je důležité, pokud chcete ověřit, že soubor XML pochází z určitého zdroje. Pokud například používáte burzovní službu, která používá XML, můžete ověřit zdroj XML, pokud je podepsaný.

Třídy v tomto oboru názvů následují [syntax XML-Signature a zpracovává doporučení](https://www.w3.org/TR/xmldsig-core/) od konsorcium World Wide Web.

## <a name="verifying-signatures"></a>Ověřování podpisů

Chcete-li ověřit, zda byla data podepsána konkrétní stranou, je nutné mít následující informace:

- Veřejný klíč strany, která podepsala data.

- Digitální podpis.

- Data, která byla podepsána.

- Algoritmus hash používaný podepsáním.

Chcete-li ověřit podpis podepsaný <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> třídou, použijte <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> třídu. <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter>Třídě musí být dodán veřejný klíč podepsaného. K určení veřejného klíče budete potřebovat hodnoty zbytku a exponentu. (Strana, která vygenerovala pár veřejného a privátního klíče, by měla poskytnout tyto hodnoty.) Nejprve vytvořte <xref:System.Security.Cryptography.RSACryptoServiceProvider> objekt, který bude obsahovat veřejný klíč, který ověří podpis, a poté inicializuje <xref:System.Security.Cryptography.RSAParameters> strukturu na hodnoty modulu a exponentu, které určují veřejný klíč.

Následující kód ukazuje vytvoření <xref:System.Security.Cryptography.RSAParameters> struktury. `Modulus`Vlastnost je nastavena na hodnotu s názvem bajtového pole `modulusData` a `Exponent` vlastnost je nastavena na hodnotu s názvem bajtového pole `exponentData` .

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

Po vytvoření <xref:System.Security.Cryptography.RSAParameters> objektu můžete inicializovat novou instanci <xref:System.Security.Cryptography.RSACryptoServiceProvider> třídy na hodnoty, které jsou zadány v <xref:System.Security.Cryptography.RSAParameters> . <xref:System.Security.Cryptography.RSACryptoServiceProvider>Je zase předán do konstruktoru <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> pro přenos klíče.

Následující příklad znázorňuje tento proces. V tomto příkladu `hashValue` `signedHashValue` jsou pole bajtů poskytnuté vzdálenou stranou. Vzdálená strana podepsala certifikát `hashValue` pomocí algoritmu SHA1 a vytvořil digitální podpis `signedHashValue` . <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType>Metoda ověřuje, zda je digitální podpis platný a byl použit k podepsání `hashValue` .

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

Tento fragment kódu zobrazí " `The signature is valid` ", pokud je podpis platný a " `The signature is not valid` ", pokud není.

## <a name="see-also"></a>Viz také

- [Kryptografické služby](cryptographic-services.md)
