---
ms.openlocfilehash: 2fb980c8b75e25ba347c56ccc1c90f2959e83e21
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567987"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a><span data-ttu-id="9d60b-101">Minimální velikost pro generování klíčů RSAOpenSsl se zvýšila</span><span class="sxs-lookup"><span data-stu-id="9d60b-101">Minimum size for RSAOpenSsl key generation has increased</span></span>

<span data-ttu-id="9d60b-102">Minimální velikost pro generování nových klíčů RSA v Systému Linux se zvýšila z 384bitového na 512bitový.</span><span class="sxs-lookup"><span data-stu-id="9d60b-102">The minimum size for generating new RSA keys on Linux has increased from 384-bit to 512-bit.</span></span>

#### <a name="change-description"></a><span data-ttu-id="9d60b-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="9d60b-103">Change description</span></span>

<span data-ttu-id="9d60b-104">Počínaje rozhraním .NET Core 3.0 se minimální `LegalKeySizes` velikost zákonného klíče <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>vykázaná vlastností v instancích RSA z aplikace , a <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A?displayProperty=nameWithType> v systému Linux zvýšila z 384 na 512.</span><span class="sxs-lookup"><span data-stu-id="9d60b-104">Starting with .NET Core 3.0, the minimum legal key size reported by the `LegalKeySizes` property on RSA instances from <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>, <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>, and <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A?displayProperty=nameWithType> on Linux has increased from 384 to 512.</span></span>

<span data-ttu-id="9d60b-105">V důsledku toho v .NET Core 2.2 a starší `RSA.Create(384)` verze, volání metody, jako je například úspěšné.</span><span class="sxs-lookup"><span data-stu-id="9d60b-105">As a result, in .NET Core 2.2 and earlier versions, a method call such as `RSA.Create(384)` succeeds.</span></span> <span data-ttu-id="9d60b-106">V .NET Core 3.0 a novější `RSA.Create(384)` verze volání metody vyvolá výjimku označující velikost je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="9d60b-106">In .NET Core 3.0 and later versions, the method call `RSA.Create(384)` throws an exception indicating the size is too small.</span></span>

<span data-ttu-id="9d60b-107">Tato změna byla provedena, protože OpenSSL, který provádí kryptografické operace na Linuxu, zvýšil své minimum mezi verzemi 1.0.2 a 1.1.0.</span><span class="sxs-lookup"><span data-stu-id="9d60b-107">This change was made because OpenSSL, which performs the cryptographic operations on Linux, raised its minimum between versions 1.0.2 and 1.1.0.</span></span> <span data-ttu-id="9d60b-108">.NET Core 3.0 preferuje OpenSSL 1.1.x až 1.0.x a minimální hlášená verze byla vyvolána tak, aby odrážela toto nové vyšší omezení závislostí.</span><span class="sxs-lookup"><span data-stu-id="9d60b-108">.NET Core 3.0 prefers OpenSSL 1.1.x to 1.0.x, and the minimum reported version was raised to reflect this new higher dependency limitation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9d60b-109">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="9d60b-109">Version introduced</span></span>

<span data-ttu-id="9d60b-110">3.0</span><span class="sxs-lookup"><span data-stu-id="9d60b-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9d60b-111">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="9d60b-111">Recommended action</span></span>

<span data-ttu-id="9d60b-112">Pokud zavoláte některou z ohrožených api, ujistěte se, že velikost všech generovaných klíčů není menší než minimální zprostředkovatel.</span><span class="sxs-lookup"><span data-stu-id="9d60b-112">If you call any of the affected APIs, ensure that the size of any generated keys is not less than the provider minimum.</span></span>

> [!NOTE]
> <span data-ttu-id="9d60b-113">384bitové RSA je již považováno za nejisté (stejně jako 512bitové RSA).</span><span class="sxs-lookup"><span data-stu-id="9d60b-113">384-bit RSA is already considered insecure (as is 512-bit RSA).</span></span> <span data-ttu-id="9d60b-114">Moderní doporučení, jako je [například NIST Special Publication 800-57 Část 1 Revize 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), naznačují 2048-bit jako minimální velikost pro nově generované klíče.</span><span class="sxs-lookup"><span data-stu-id="9d60b-114">Modern recommendations, such as [NIST Special Publication 800-57 Part 1 Revision 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), suggest 2048-bit as the minimum size for newly generated keys.</span></span>

#### <a name="category"></a><span data-ttu-id="9d60b-115">Kategorie</span><span class="sxs-lookup"><span data-stu-id="9d60b-115">Category</span></span>

<span data-ttu-id="9d60b-116">Kryptografie</span><span class="sxs-lookup"><span data-stu-id="9d60b-116">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9d60b-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="9d60b-117">Affected APIs</span></span>

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
