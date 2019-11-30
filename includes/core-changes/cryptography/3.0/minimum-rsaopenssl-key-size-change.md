---
ms.openlocfilehash: 2fb980c8b75e25ba347c56ccc1c90f2959e83e21
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567987"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a>Minimální velikost pro generování klíče RSAOpenSsl se zvýšila.

Minimální velikost pro generování nových klíčů RSA v systému Linux se zvýšila z 384-bitů na 512.

#### <a name="change-description"></a>Změnit popis

Počínaje rozhraním .NET Core 3,0 se minimální velikost klíčového klíče hlášená vlastností `LegalKeySizes` na instancích RSA z <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>, <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>a <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A?displayProperty=nameWithType> systému Linux zvýšila z 384 na 512.

V důsledku toho se v .NET Core 2,2 a starších verzích volání metody, jako je `RSA.Create(384)`, zdaří. V rozhraní .NET Core 3,0 a novějších verzích `RSA.Create(384)` volání metody vyvolá výjimku oznamující, že velikost je příliš malá.

Tato změna byla provedena, protože OpenSSL, která provádí kryptografické operace v systému Linux, vyvolala minimální verzi 1.0.2 a 1.1.0. .NET Core 3,0 preferuje OpenSSL 1.1. x až 1.0. x a minimální nahlášená verze se vyvolala, aby odrážela toto nové omezení vyšší závislosti.

#### <a name="version-introduced"></a>Představená verze

3,0

#### <a name="recommended-action"></a>Doporučená akce

Pokud voláte kterékoli z ovlivněných rozhraní API, ujistěte se, že velikost vygenerovaných klíčů není menší než minimum poskytovatele.

> [!NOTE]
> 384 bit RSA se už považuje za nezabezpečený (jako je to 512 bitů RSA). Moderní doporučení, jako je [NIST Special publikace 800-57 část 1 revize 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), navrhují 2048-bit jako minimální velikost pro nově vygenerované klíče.

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
