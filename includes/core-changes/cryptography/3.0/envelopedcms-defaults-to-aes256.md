---
ms.openlocfilehash: d23c6cc9f8ee9c912ce5c9509d157692d1a18f90
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721302"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a><span data-ttu-id="17e20-101">EnvelopedCms ve výchozím nastavení šifrování AES-256</span><span class="sxs-lookup"><span data-stu-id="17e20-101">EnvelopedCms defaults to AES-256 encryption</span></span>

<span data-ttu-id="17e20-102">Výchozí symetrický šifrovací algoritmus používaný nástrojem `EnvelopedCms` se změnil z TripleDES na AES-256.</span><span class="sxs-lookup"><span data-stu-id="17e20-102">The default symmetric encryption algorithm used by `EnvelopedCms` has changed from TripleDES to AES-256.</span></span>

#### <a name="change-description"></a><span data-ttu-id="17e20-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="17e20-103">Change description</span></span>

<span data-ttu-id="17e20-104">V .NET Core Preview 7 a starších verzích, když <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> se používá k šifrování dat bez určení symetrického šifrovacího algoritmu prostřednictvím přetížení konstruktoru, se data šifrují pomocí algoritmu TripleDES/3DES/3DEA/DES3-Ede.</span><span class="sxs-lookup"><span data-stu-id="17e20-104">In .NET Core Preview 7 and earlier versions, when <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> is used to encrypt data without specifying a symmetric encryption algorithm via a constructor overload, the data was encrypted with the TripleDES/3DES/3DEA/DES3-EDE algorithm.</span></span>

<span data-ttu-id="17e20-105">Počínaje rozhraním .NET Core 3,0 Preview 8 (přes 4.6.0 verze balíčku [System. Security. Cryptography. PKCS](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) ) se výchozí algoritmus změnil na AES-256 pro modernizaci algoritmu a pro zlepšení zabezpečení výchozích možností.</span><span class="sxs-lookup"><span data-stu-id="17e20-105">Starting with .NET Core 3.0 Preview 8 (via version 4.6.0 of the [System.Security.Cryptography.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet package), the default algorithm has been changed to AES-256 for algorithm modernization and to improve the security of default options.</span></span> <span data-ttu-id="17e20-106">Pokud má certifikát příjemce zprávy (jiný než EC) veřejný klíč Diffie-Hellman, může operace šifrování selhat a <xref:System.Security.Cryptography.CryptographicException> v důsledku omezení v základní platformě.</span><span class="sxs-lookup"><span data-stu-id="17e20-106">If a message recipient certificate has a (non-EC) Diffie-Hellman public key, the encryption operation may fail with a <xref:System.Security.Cryptography.CryptographicException> due to limitations in the underlying platform.</span></span>

<span data-ttu-id="17e20-107">V následujícím ukázkovém kódu jsou data při použití v rozhraní .NET Core 3,0 Preview 7 nebo starší zašifrovaná pomocí TripleDES.</span><span class="sxs-lookup"><span data-stu-id="17e20-107">In the following sample code, the data is encrypted with TripleDES if running on .NET Core 3.0 Preview 7 or earlier.</span></span> <span data-ttu-id="17e20-108">Pokud používáte .NET Core 3,0 Preview 8 nebo novější, je zašifrovaný pomocí AES-256.</span><span class="sxs-lookup"><span data-stu-id="17e20-108">If running on .NET Core 3.0 Preview 8 or later, it is encrypted with AES-256.</span></span>

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a><span data-ttu-id="17e20-109">Představená verze</span><span class="sxs-lookup"><span data-stu-id="17e20-109">Version introduced</span></span>

<span data-ttu-id="17e20-110">3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="17e20-110">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="17e20-111">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="17e20-111">Recommended action</span></span>

<span data-ttu-id="17e20-112">Pokud se změnou negativně neovlivní změna, můžete šifrování TripleDES obnovit explicitním zadáním identifikátoru šifrovacího algoritmu v <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> konstruktoru, který obsahuje parametr typu <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier> , například:</span><span class="sxs-lookup"><span data-stu-id="17e20-112">If you are negatively impacted by the change, you can restore TripleDES encryption by explicitly specifying the encryption algorithm identifier in an <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> constructor that includes a parameter of type <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>, such as:</span></span>

```csharp
Oid tripleDesOid = new Oid("1.2.840.113549.3.7", null);
AlgorithmIdentifier tripleDesIdentifier = new AlgorithmIdentifier(tripleDesOid);
EnvelopedCms cms = new EnvelopedCms(content, tripleDesIdentifier);

cms.Encrypt(recipient);
return cms.Encode()l
```

#### <a name="category"></a><span data-ttu-id="17e20-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="17e20-113">Category</span></span>

<span data-ttu-id="17e20-114">Kryptografie</span><span class="sxs-lookup"><span data-stu-id="17e20-114">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="17e20-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="17e20-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.ContentInfo)>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->
