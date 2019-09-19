---
ms.openlocfilehash: 07ab65de16b72bd0844a39e4b35235c5f043f3ec
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117224"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a>Minimální velikost pro generování klíče RSAOpenSsl se zvýšila.

Minimální velikost pro generování nových klíčů RSA v systému Linux se zvýšila z 384-bitů na 512.

#### <a name="change-description"></a>Změnit popis

Počínaje rozhraním .NET Core 3,0 je minimální velikost klíčového klíče hlášená `LegalKeySizes` vlastností na instancích RSA z < System. Security. Cryptography. RSA. Create% 2a? displayProperty = nameWithType >, < System. Security. Cryptography. RSAOpenSsl.% 23ctor% 2A? displayProperty = nameWithType > a < System. Security. Cryptography. RSACryptoServicePlatform.% 23ctor% 2A? displayProperty = nameWithType > on Linux se zvýšila z 384 na 512.

V důsledku toho se v .NET Core 2,2 a dřívějších verzích volání `RSA.Create(384)` metody, jako je například úspěch. V rozhraní .NET Core 3,0 a novějších verzích vyvolá volání `RSA.Create(384)` metody výjimku oznamující, že velikost je příliš malá.

Tyto změny byly provedeny, protože OpenSSL, které provádí kryptografické operace v systému Linux, vyvolala minimální verzi 1.0.2 a 1.1.0.  .NET Core 3,0 preferuje OpenSSL 1.1. x až 1.0. x a minimální nahlášená verze se vyvolala, aby odrážela toto nové omezení vyšší závislosti.

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Pokud voláte kterékoli z ovlivněných rozhraní API, ujistěte se, že velikost vygenerovaných klíčů není menší než minimum poskytovatele.

> [!NOTE]
> 384 bit RSA se už považuje za nezabezpečený (jako je to 512 bitů RSA). Moderní doporučení, jako je [NIST Special publikace 800-57 část 1 revize 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), navrhují 2048-bit jako minimální velikost pro nově vygenerované klíče.

#### <a name="category"></a>Kategorie

Kryptografick

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
