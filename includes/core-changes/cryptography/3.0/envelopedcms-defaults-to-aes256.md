---
ms.openlocfilehash: b90991affe158286f535f3cc17232efd0b730fec
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81274929"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a><span data-ttu-id="5f88c-101">Standardy EnvelopedCms jsou výchozí pro šifrování AES-256</span><span class="sxs-lookup"><span data-stu-id="5f88c-101">EnvelopedCms defaults to AES-256 encryption</span></span>

<span data-ttu-id="5f88c-102">Výchozí algoritmus symetrického šifrování, který používá, `EnvelopedCms` se změnil z TripleDES na AES-256.</span><span class="sxs-lookup"><span data-stu-id="5f88c-102">The default symmetric encryption algorithm used by `EnvelopedCms` has changed from TripleDES to AES-256.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5f88c-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="5f88c-103">Change description</span></span>

<span data-ttu-id="5f88c-104">V .NET Core Preview 7 a <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> starších verzích, když se používá k šifrování dat bez zadání algoritmu symetrického šifrování prostřednictvím přetížení konstruktoru, byla data zašifrována algoritmem TripleDES/3DES/3DEA/DES3-EDE.</span><span class="sxs-lookup"><span data-stu-id="5f88c-104">In .NET Core Preview 7 and earlier versions, when <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> is used to encrypt data without specifying a symmetric encryption algorithm via a constructor overload, the data was encrypted with the TripleDES/3DES/3DEA/DES3-EDE algorithm.</span></span>

<span data-ttu-id="5f88c-105">Počínaje rozhraním .NET Core 3.0 Preview 8 (prostřednictvím verze 4.6.0 balíčku [System.Security.Cryptography.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet) byl výchozí algoritmus změněn na AES-256 pro modernizaci algoritmu a zlepšení zabezpečení výchozích možností.</span><span class="sxs-lookup"><span data-stu-id="5f88c-105">Starting with .NET Core 3.0 Preview 8 (via version 4.6.0 of the [System.Security.Cryptography.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet package), the default algorithm has been changed to AES-256 for algorithm modernization and to improve the security of default options.</span></span> <span data-ttu-id="5f88c-106">Pokud má certifikát příjemce zprávy (non-ES) Diffie-Hellman veřejný klíč, <xref:System.Security.Cryptography.CryptographicException> operace šifrování může selhat s z důvodu omezení v podkladové platformě.</span><span class="sxs-lookup"><span data-stu-id="5f88c-106">If a message recipient certificate has a (non-EC) Diffie-Hellman public key, the encryption operation may fail with a <xref:System.Security.Cryptography.CryptographicException> due to limitations in the underlying platform.</span></span>

<span data-ttu-id="5f88c-107">V následujícím ukázkovém kódu jsou data šifrována pomocí TripleDES, pokud jsou spuštěna na rozhraní .NET Core 3.0 Preview 7 nebo starší.</span><span class="sxs-lookup"><span data-stu-id="5f88c-107">In the following sample code, the data is encrypted with TripleDES if running on .NET Core 3.0 Preview 7 or earlier.</span></span> <span data-ttu-id="5f88c-108">Pokud běží na .NET Core 3.0 Náhled 8 nebo novější, je šifrován s AES-256.</span><span class="sxs-lookup"><span data-stu-id="5f88c-108">If running on .NET Core 3.0 Preview 8 or later, it is encrypted with AES-256.</span></span>

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a><span data-ttu-id="5f88c-109">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="5f88c-109">Version introduced</span></span>

<span data-ttu-id="5f88c-110">3.0 Náhled 8</span><span class="sxs-lookup"><span data-stu-id="5f88c-110">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5f88c-111">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="5f88c-111">Recommended action</span></span>

<span data-ttu-id="5f88c-112">Pokud jste negativně ovlivněni změnou, můžete obnovit šifrování TripleDES explicitním zadáním <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> identifikátoru šifrovacího algoritmu v konstruktoru, který obsahuje parametr typu <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>, například:</span><span class="sxs-lookup"><span data-stu-id="5f88c-112">If you are negatively impacted by the change, you can restore TripleDES encryption by explicitly specifying the encryption algorithm identifier in an <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> constructor that includes a parameter of type <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>, such as:</span></span>

```csharp
Oid tripleDesOid = new Oid("1.2.840.113549.3.7", null);
AlgorithmIdentifier tripleDesIdentifier = new AlgorithmIdentifier(tripleDesOid);
EnvelopedCms cms = new EnvelopedCms(content, tripleDesIdentifier);

cms.Encrypt(recipient);
return cms.Encode()l
```

#### <a name="category"></a><span data-ttu-id="5f88c-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="5f88c-113">Category</span></span>

<span data-ttu-id="5f88c-114">Kryptografie</span><span class="sxs-lookup"><span data-stu-id="5f88c-114">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5f88c-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="5f88c-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.ContentInfo)>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->
