---
ms.openlocfilehash: f9000b19997201c2d3de0643669f9029ff1ca31c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567975"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a>Standardy EnvelopedCms jsou výchozí pro šifrování AES-256

Výchozí algoritmus symetrického šifrování, který používá, `EnvelopedCms` se změnil z TripleDES na AES-256.

#### <a name="change-description"></a>Popis změny

V .NET Core Preview 7 a <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> starších verzích, když se používá k šifrování dat bez zadání algoritmu symetrického šifrování prostřednictvím přetížení konstruktoru, byla data zašifrována algoritmem TripleDES/3DES/3DEA/DES3-EDE.

Počínaje rozhraním .NET Core 3.0 Preview 8 (prostřednictvím verze 4.6.0 balíčku [System.Security.Cryptography.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet) byl výchozí algoritmus změněn na AES-256 pro modernizaci algoritmu a zlepšení zabezpečení výchozích možností. Pokud má certifikát příjemce zprávy (non-ES) Diffie-Hellman veřejný klíč, <xref:System.Security.Cryptography.CryptographicException> operace šifrování může selhat s z důvodu omezení v podkladové platformě.

V následujícím ukázkovém kódu jsou data šifrována pomocí TripleDES, pokud jsou spuštěna na rozhraní .NET Core 3.0 Preview 7 nebo starší. Pokud běží na .NET Core 3.0 Náhled 8 nebo novější, je šifrován s AES-256.

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a>Zavedená verze

3.0 Náhled 8

#### <a name="recommended-action"></a>Doporučená akce

Pokud jste negativně ovlivněni změnou, můžete obnovit šifrování TripleDES explicitním zadáním <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> identifikátoru šifrovacího algoritmu v konstruktoru, který obsahuje parametr typu <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>, například:

```csharp
Oid tripleDesOid = new Oid("1.2.840.113549.3.7", null);
AlgorithmIdentifier tripleDesIdentifier = new AlgorithmIdentifier(tripleDesOid);
EnvelopedCms cms = new EnvelopedCms(content, tripleDesIdentifier);

cms.Encrypt(recipient);
return cms.Encode()l
```

#### <a name="category"></a>Kategorie

Kryptografie

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.ContentInfo)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->
