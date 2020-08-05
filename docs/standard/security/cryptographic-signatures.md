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
# <a name="cryptographic-signatures"></a>Kryptografické podpisy

Kryptografické digitální podpisy využívají algoritmy veřejného klíče k zajištění integrity dat. Když podepisujete data digitálním podpisem, někdo jiný může podpis ověřit a může prokázat, že data pocházejí z vás a že se po jejím podepsání nezměnila. Další informace o digitálních podpisech najdete v tématu [kryptografické služby](cryptographic-services.md).

Toto téma vysvětluje, jak vygenerovat a ověřit digitální podpisy pomocí tříd v <xref:System.Security.Cryptography> oboru názvů.

## <a name="generating-signatures"></a>Generování podpisů

Digitální podpisy jsou obvykle aplikovány na hodnoty hash, které představují větší data. Následující příklad aplikuje digitální podpis na hodnotu hash. Nejprve se vytvoří nová instance třídy, <xref:System.Security.Cryptography.RSA> která vygeneruje pár veřejného a privátního klíče. Dále <xref:System.Security.Cryptography.RSA> je předána do nové instance <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> třídy. Tím se privátní klíč přenáší do <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> , který skutečně provádí digitální podepisování. Než budete moci podepsat kód hash, je nutné zadat algoritmus hash, který se má použít. V tomto příkladu se používá algoritmus SHA1. Nakonec <xref:System.Security.Cryptography.AsymmetricSignatureFormatter.CreateSignature%2A> je volána metoda pro provedení podepisování.

Z důvodu kolizí problémů se SHA1 doporučujeme SHA256 nebo lepší.

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

## <a name="verifying-signatures"></a>Ověřování podpisů

Chcete-li ověřit, zda byla data podepsána konkrétní stranou, je nutné mít následující informace:

- Veřejný klíč strany, která podepsala data.

- Digitální podpis.

- Data, která byla podepsána.

- Algoritmus hash používaný podepsáním.

Chcete-li ověřit podpis podepsaný <xref:System.Security.Cryptography.RSAPKCS1SignatureFormatter> třídou, použijte <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> třídu. <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter>Třídě musí být dodán veřejný klíč podepsaného. Pro RSA budete potřebovat hodnoty zbytku a exponentu k určení veřejného klíče. (Strana, která vygenerovala pár veřejného a privátního klíče, by měla poskytnout tyto hodnoty.) Nejprve vytvořte <xref:System.Security.Cryptography.RSA> objekt, který bude obsahovat veřejný klíč, který ověří podpis, a poté inicializuje <xref:System.Security.Cryptography.RSAParameters> strukturu na hodnoty modulu a exponentu, které určují veřejný klíč.

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

Po vytvoření <xref:System.Security.Cryptography.RSAParameters> objektu můžete inicializovat novou instanci <xref:System.Security.Cryptography.RSA> implementační třídy na hodnoty, které jsou zadány v <xref:System.Security.Cryptography.RSAParameters> . <xref:System.Security.Cryptography.RSA>Instance je zase předána konstruktoru <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter> pro přenos klíče.

Následující příklad znázorňuje tento proces. V tomto příkladu `hashValue` `signedHashValue` jsou pole bajtů poskytnuté vzdálenou stranou. Vzdálená strana podepsala certifikát `hashValue` pomocí algoritmu SHA1 a vytvořil digitální podpis `signedHashValue` . <xref:System.Security.Cryptography.RSAPKCS1SignatureDeformatter.VerifySignature%2A?displayProperty=nameWithType>Metoda ověřuje, zda je digitální podpis platný a byl použit k podepsání `hashValue` .

Z důvodu kolizí problémů se SHA1 doporučujeme SHA256 nebo lepší.  Pokud se ale pomocí algoritmu SHA1 vytvořil podpis, musíte k ověření podpisu použít SHA1.

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

Tento fragment kódu zobrazí " `The signature is valid` ", pokud je podpis platný a " `The signature is not valid` ", pokud není.

## <a name="see-also"></a>Viz také

- [Šifrovací služby](cryptographic-services.md)
- [Kryptografický model](cryptography-model.md)
- [Kryptografie pro různé platformy](cross-platform-cryptography.md)
- [Ochrana dat ASP.NET Core](/aspnet/core/security/data-protection/introduction)
