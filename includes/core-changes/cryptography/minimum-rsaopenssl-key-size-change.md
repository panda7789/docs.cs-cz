---
ms.openlocfilehash: 07ab65de16b72bd0844a39e4b35235c5f043f3ec
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117224"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a><span data-ttu-id="1ed53-101">Minimální velikost pro generování klíče RSAOpenSsl se zvýšila.</span><span class="sxs-lookup"><span data-stu-id="1ed53-101">Minimum size for RSAOpenSsl key generation has increased</span></span>

<span data-ttu-id="1ed53-102">Minimální velikost pro generování nových klíčů RSA v systému Linux se zvýšila z 384-bitů na 512.</span><span class="sxs-lookup"><span data-stu-id="1ed53-102">The minimum size for generating new RSA keys on Linux has increased from 384-bit to 512-bit.</span></span>

#### <a name="change-description"></a><span data-ttu-id="1ed53-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="1ed53-103">Change description</span></span>

<span data-ttu-id="1ed53-104">Počínaje rozhraním .NET Core 3,0 je minimální velikost klíčového klíče hlášená `LegalKeySizes` vlastností na instancích RSA z < System. Security. Cryptography. RSA. Create% 2a? displayProperty = nameWithType >, < System. Security. Cryptography. RSAOpenSsl.% 23ctor% 2A? displayProperty = nameWithType > a < System. Security. Cryptography. RSACryptoServicePlatform.% 23ctor% 2A? displayProperty = nameWithType > on Linux se zvýšila z 384 na 512.</span><span class="sxs-lookup"><span data-stu-id="1ed53-104">Starting with .NET Core 3.0, the minimum legal key size reported by the `LegalKeySizes` property on RSA instances from <System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>, <System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>, and <System.Security.Cryptography.RSACryptoServicePlatform.%23ctor%2A?displayProperty=nameWithType> on Linux has increased from 384 to 512.</span></span>

<span data-ttu-id="1ed53-105">V důsledku toho se v .NET Core 2,2 a dřívějších verzích volání `RSA.Create(384)` metody, jako je například úspěch.</span><span class="sxs-lookup"><span data-stu-id="1ed53-105">As a result, in .NET Core 2.2 and earlier versions, a method call such as `RSA.Create(384)` succeeds.</span></span> <span data-ttu-id="1ed53-106">V rozhraní .NET Core 3,0 a novějších verzích vyvolá volání `RSA.Create(384)` metody výjimku oznamující, že velikost je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="1ed53-106">In .NET Core 3.0 and later versions, the method call `RSA.Create(384)` throws an exception indicating the size is too small.</span></span>

<span data-ttu-id="1ed53-107">Tyto změny byly provedeny, protože OpenSSL, které provádí kryptografické operace v systému Linux, vyvolala minimální verzi 1.0.2 a 1.1.0.</span><span class="sxs-lookup"><span data-stu-id="1ed53-107">This changes was made because OpenSSL, which performs the cryptographic operations on Linux, raised its minimum between versions 1.0.2 and 1.1.0.</span></span>  <span data-ttu-id="1ed53-108">.NET Core 3,0 preferuje OpenSSL 1.1. x až 1.0. x a minimální nahlášená verze se vyvolala, aby odrážela toto nové omezení vyšší závislosti.</span><span class="sxs-lookup"><span data-stu-id="1ed53-108">.NET Core 3.0 prefers OpenSSL 1.1.x to 1.0.x, and the minimum reported version was raised to reflect this new higher dependency limitation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1ed53-109">Představená verze</span><span class="sxs-lookup"><span data-stu-id="1ed53-109">Version introduced</span></span>

<span data-ttu-id="1ed53-110">3.0</span><span class="sxs-lookup"><span data-stu-id="1ed53-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1ed53-111">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="1ed53-111">Recommended action</span></span>

<span data-ttu-id="1ed53-112">Pokud voláte kterékoli z ovlivněných rozhraní API, ujistěte se, že velikost vygenerovaných klíčů není menší než minimum poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="1ed53-112">If you call any of the affected APIs, ensure that the size of any generated keys is not less than the provider minimum.</span></span>

> [!NOTE]
> <span data-ttu-id="1ed53-113">384 bit RSA se už považuje za nezabezpečený (jako je to 512 bitů RSA).</span><span class="sxs-lookup"><span data-stu-id="1ed53-113">384-bit RSA is already considered insecure (as is 512-bit RSA).</span></span> <span data-ttu-id="1ed53-114">Moderní doporučení, jako je [NIST Special publikace 800-57 část 1 revize 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), navrhují 2048-bit jako minimální velikost pro nově vygenerované klíče.</span><span class="sxs-lookup"><span data-stu-id="1ed53-114">Modern recommendations, such as [NIST Special Publication 800-57 Part 1 Revision 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), suggest 2048-bit as the minimum size for newly generated keys.</span></span>

#### <a name="category"></a><span data-ttu-id="1ed53-115">Kategorie</span><span class="sxs-lookup"><span data-stu-id="1ed53-115">Category</span></span>

<span data-ttu-id="1ed53-116">Kryptografick</span><span class="sxs-lookup"><span data-stu-id="1ed53-116">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1ed53-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="1ed53-117">Affected APIs</span></span>

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
