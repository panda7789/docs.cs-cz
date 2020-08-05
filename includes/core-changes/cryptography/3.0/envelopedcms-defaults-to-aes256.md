---
ms.openlocfilehash: e0cdcce9b8c7d591925b08635e3354dadaf22b7b
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556021"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a>EnvelopedCms ve výchozím nastavení šifrování AES-256

Výchozí symetrický šifrovací algoritmus používaný nástrojem `EnvelopedCms` se změnil z TripleDES na AES-256.

#### <a name="change-description"></a>Popis změny

V předchozích verzích, kdy <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> se používá k šifrování dat bez určení symetrického šifrovacího algoritmu prostřednictvím přetížení konstruktoru, jsou data zašifrovaná pomocí algoritmu TripleDES/3DES/3DEA/DES3-Ede.

Počínaje .NET Core 3,0 (přes 4.6.0 verze balíčku [System. Security. Cryptography. PKCS](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) ) se výchozí algoritmus změnil na AES-256 pro modernizaci algoritmu a pro zlepšení zabezpečení výchozích možností. Pokud má certifikát příjemce zprávy (jiný než EC) veřejný klíč Diffie-Hellman, může operace šifrování selhat a <xref:System.Security.Cryptography.CryptographicException> v důsledku omezení v základní platformě.

V následujícím ukázkovém kódu jsou data při použití v rozhraní .NET Core 2,2 nebo starší zašifrovaná pomocí TripleDES. Pokud používáte .NET Core 3,0 nebo novější, je šifrovaný pomocí AES-256.

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Pokud se změnou negativně neovlivní změna, můžete šifrování TripleDES obnovit explicitním zadáním identifikátoru šifrovacího algoritmu v <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> konstruktoru, který obsahuje parametr typu <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier> , například:

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

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.ContentInfo)>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->
