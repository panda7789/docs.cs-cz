---
ms.openlocfilehash: e3bda3cf6319d8c988b6c897b78869f517f9616a
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181997"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a><span data-ttu-id="c98f6-101">Minimální velikost pro generování klíče RSAOpenSsl se zvýšila.</span><span class="sxs-lookup"><span data-stu-id="c98f6-101">Minimum size for RSAOpenSsl key generation has increased</span></span>

<span data-ttu-id="c98f6-102">Minimální velikost pro generování nových klíčů RSA v systému Linux se zvýšila z 384-bitů na 512.</span><span class="sxs-lookup"><span data-stu-id="c98f6-102">The minimum size for generating new RSA keys on Linux has increased from 384-bit to 512-bit.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c98f6-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="c98f6-103">Change description</span></span>

<span data-ttu-id="c98f6-104">Počínaje rozhraním .NET Core 3,0 se minimální velikost klíčového klíče hlášená `LegalKeySizes` vlastností na instancích RSA <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>od <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>, a <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A?displayProperty=nameWithType> v systému Linux zvýšila z 384 na 512.</span><span class="sxs-lookup"><span data-stu-id="c98f6-104">Starting with .NET Core 3.0, the minimum legal key size reported by the `LegalKeySizes` property on RSA instances from <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>, <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>, and <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A?displayProperty=nameWithType> on Linux has increased from 384 to 512.</span></span>

<span data-ttu-id="c98f6-105">V důsledku toho se v .NET Core 2,2 a dřívějších verzích volání `RSA.Create(384)` metody, jako je například úspěch.</span><span class="sxs-lookup"><span data-stu-id="c98f6-105">As a result, in .NET Core 2.2 and earlier versions, a method call such as `RSA.Create(384)` succeeds.</span></span> <span data-ttu-id="c98f6-106">V rozhraní .NET Core 3,0 a novějších verzích vyvolá volání `RSA.Create(384)` metody výjimku oznamující, že velikost je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="c98f6-106">In .NET Core 3.0 and later versions, the method call `RSA.Create(384)` throws an exception indicating the size is too small.</span></span>

<span data-ttu-id="c98f6-107">Tato změna byla provedena, protože OpenSSL, která provádí kryptografické operace v systému Linux, vyvolala minimální verzi 1.0.2 a 1.1.0.</span><span class="sxs-lookup"><span data-stu-id="c98f6-107">This change was made because OpenSSL, which performs the cryptographic operations on Linux, raised its minimum between versions 1.0.2 and 1.1.0.</span></span> <span data-ttu-id="c98f6-108">.NET Core 3,0 preferuje OpenSSL 1.1. x až 1.0. x a minimální nahlášená verze se vyvolala, aby odrážela toto nové omezení vyšší závislosti.</span><span class="sxs-lookup"><span data-stu-id="c98f6-108">.NET Core 3.0 prefers OpenSSL 1.1.x to 1.0.x, and the minimum reported version was raised to reflect this new higher dependency limitation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c98f6-109">Představená verze</span><span class="sxs-lookup"><span data-stu-id="c98f6-109">Version introduced</span></span>

<span data-ttu-id="c98f6-110">3.0</span><span class="sxs-lookup"><span data-stu-id="c98f6-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c98f6-111">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="c98f6-111">Recommended action</span></span>

<span data-ttu-id="c98f6-112">Pokud voláte kterékoli z ovlivněných rozhraní API, ujistěte se, že velikost vygenerovaných klíčů není menší než minimum poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="c98f6-112">If you call any of the affected APIs, ensure that the size of any generated keys is not less than the provider minimum.</span></span>

> [!NOTE]
> <span data-ttu-id="c98f6-113">384 bit RSA se už považuje za nezabezpečený (jako je to 512 bitů RSA).</span><span class="sxs-lookup"><span data-stu-id="c98f6-113">384-bit RSA is already considered insecure (as is 512-bit RSA).</span></span> <span data-ttu-id="c98f6-114">Moderní doporučení, jako je [NIST Special publikace 800-57 část 1 revize 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), navrhují 2048-bit jako minimální velikost pro nově vygenerované klíče.</span><span class="sxs-lookup"><span data-stu-id="c98f6-114">Modern recommendations, such as [NIST Special Publication 800-57 Part 1 Revision 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), suggest 2048-bit as the minimum size for newly generated keys.</span></span>

#### <a name="category"></a><span data-ttu-id="c98f6-115">Kategorie</span><span class="sxs-lookup"><span data-stu-id="c98f6-115">Category</span></span>

<span data-ttu-id="c98f6-116">Kryptografick</span><span class="sxs-lookup"><span data-stu-id="c98f6-116">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c98f6-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="c98f6-117">Affected APIs</span></span>

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
