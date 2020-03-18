---
ms.openlocfilehash: 2fb980c8b75e25ba347c56ccc1c90f2959e83e21
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567987"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a>Minimální velikost pro generování klíčů RSAOpenSsl se zvýšila

Minimální velikost pro generování nových klíčů RSA v Systému Linux se zvýšila z 384bitového na 512bitový.

#### <a name="change-description"></a>Popis změny

Počínaje rozhraním .NET Core 3.0 se minimální `LegalKeySizes` velikost zákonného klíče <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>vykázaná vlastností v instancích RSA z aplikace , a <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A?displayProperty=nameWithType> v systému Linux zvýšila z 384 na 512.

V důsledku toho v .NET Core 2.2 a starší `RSA.Create(384)` verze, volání metody, jako je například úspěšné. V .NET Core 3.0 a novější `RSA.Create(384)` verze volání metody vyvolá výjimku označující velikost je příliš malá.

Tato změna byla provedena, protože OpenSSL, který provádí kryptografické operace na Linuxu, zvýšil své minimum mezi verzemi 1.0.2 a 1.1.0. .NET Core 3.0 preferuje OpenSSL 1.1.x až 1.0.x a minimální hlášená verze byla vyvolána tak, aby odrážela toto nové vyšší omezení závislostí.

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Pokud zavoláte některou z ohrožených api, ujistěte se, že velikost všech generovaných klíčů není menší než minimální zprostředkovatel.

> [!NOTE]
> 384bitové RSA je již považováno za nejisté (stejně jako 512bitové RSA). Moderní doporučení, jako je [například NIST Special Publication 800-57 Část 1 Revize 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), naznačují 2048-bit jako minimální velikost pro nově generované klíče.

#### <a name="category"></a>Kategorie

Kryptografie

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A?displayProperty=nameWithType>

<!--
### Affected APIs

- `P:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes`
- `Overload:System.Security.Cryptography.RSA.Create`
- `Overload:System.Security.Cryptography.RSAOpenSsl.#ctor`
- `Overload:System.Security.Cryptography.RSACryptoServiceProvider.#ctor`

-->
