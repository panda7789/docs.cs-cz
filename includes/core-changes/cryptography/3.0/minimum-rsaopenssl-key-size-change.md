---
ms.openlocfilehash: b5b724afefcce69df706f2bea0b1612db653af03
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81274917"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a><span data-ttu-id="6b8ab-101">Minimální velikost pro generování klíčů RSAOpenSsl se zvýšila</span><span class="sxs-lookup"><span data-stu-id="6b8ab-101">Minimum size for RSAOpenSsl key generation has increased</span></span>

<span data-ttu-id="6b8ab-102">Minimální velikost pro generování nových klíčů RSA v Systému Linux se zvýšila z 384bitového na 512bitový.</span><span class="sxs-lookup"><span data-stu-id="6b8ab-102">The minimum size for generating new RSA keys on Linux has increased from 384-bit to 512-bit.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6b8ab-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="6b8ab-103">Change description</span></span>

<span data-ttu-id="6b8ab-104">Počínaje rozhraním .NET Core 3.0 se minimální `LegalKeySizes` velikost zákonného klíče <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A>vykázaná vlastností v instancích RSA z aplikace , a <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A> v systému Linux zvýšila z 384 na 512.</span><span class="sxs-lookup"><span data-stu-id="6b8ab-104">Starting with .NET Core 3.0, the minimum legal key size reported by the `LegalKeySizes` property on RSA instances from <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>, <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A>, and <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A> on Linux has increased from 384 to 512.</span></span>

<span data-ttu-id="6b8ab-105">V důsledku toho v .NET Core 2.2 a starší `RSA.Create(384)` verze, volání metody, jako je například úspěšné.</span><span class="sxs-lookup"><span data-stu-id="6b8ab-105">As a result, in .NET Core 2.2 and earlier versions, a method call such as `RSA.Create(384)` succeeds.</span></span> <span data-ttu-id="6b8ab-106">V .NET Core 3.0 a novější `RSA.Create(384)` verze volání metody vyvolá výjimku označující velikost je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="6b8ab-106">In .NET Core 3.0 and later versions, the method call `RSA.Create(384)` throws an exception indicating the size is too small.</span></span>

<span data-ttu-id="6b8ab-107">Tato změna byla provedena, protože OpenSSL, který provádí kryptografické operace na Linuxu, zvýšil své minimum mezi verzemi 1.0.2 a 1.1.0.</span><span class="sxs-lookup"><span data-stu-id="6b8ab-107">This change was made because OpenSSL, which performs the cryptographic operations on Linux, raised its minimum between versions 1.0.2 and 1.1.0.</span></span> <span data-ttu-id="6b8ab-108">.NET Core 3.0 preferuje OpenSSL 1.1.x až 1.0.x a minimální hlášená verze byla vyvolána tak, aby odrážela toto nové vyšší omezení závislostí.</span><span class="sxs-lookup"><span data-stu-id="6b8ab-108">.NET Core 3.0 prefers OpenSSL 1.1.x to 1.0.x, and the minimum reported version was raised to reflect this new higher dependency limitation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6b8ab-109">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="6b8ab-109">Version introduced</span></span>

<span data-ttu-id="6b8ab-110">3.0</span><span class="sxs-lookup"><span data-stu-id="6b8ab-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6b8ab-111">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="6b8ab-111">Recommended action</span></span>

<span data-ttu-id="6b8ab-112">Pokud zavoláte některou z ohrožených api, ujistěte se, že velikost všech generovaných klíčů není menší než minimální zprostředkovatel.</span><span class="sxs-lookup"><span data-stu-id="6b8ab-112">If you call any of the affected APIs, ensure that the size of any generated keys is not less than the provider minimum.</span></span>

> [!NOTE]
> <span data-ttu-id="6b8ab-113">384bitové RSA je již považováno za nejisté (stejně jako 512bitové RSA).</span><span class="sxs-lookup"><span data-stu-id="6b8ab-113">384-bit RSA is already considered insecure (as is 512-bit RSA).</span></span> <span data-ttu-id="6b8ab-114">Moderní doporučení, jako je [například NIST Special Publication 800-57 Část 1 Revize 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), naznačují 2048-bit jako minimální velikost pro nově generované klíče.</span><span class="sxs-lookup"><span data-stu-id="6b8ab-114">Modern recommendations, such as [NIST Special Publication 800-57 Part 1 Revision 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), suggest 2048-bit as the minimum size for newly generated keys.</span></span>

#### <a name="category"></a><span data-ttu-id="6b8ab-115">Kategorie</span><span class="sxs-lookup"><span data-stu-id="6b8ab-115">Category</span></span>

<span data-ttu-id="6b8ab-116">Kryptografie</span><span class="sxs-lookup"><span data-stu-id="6b8ab-116">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6b8ab-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="6b8ab-117">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A>
- <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A>

<!--
### Affected APIs

- `P:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes`
- `Overload:System.Security.Cryptography.RSA.Create`
- `Overload:System.Security.Cryptography.RSAOpenSsl.#ctor`
- `Overload:System.Security.Cryptography.RSACryptoServiceProvider.#ctor`

-->
