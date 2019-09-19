---
ms.openlocfilehash: d80eb6923b1cafee248c25748915166bafd64817
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117168"
---
### <a name="net-core-30-prefers-openssl-11x-to-openssl-10x"></a><span data-ttu-id="e7b97-101">.NET Core 3,0 upřednostňuje OpenSSL 1.1. x až OpenSSL 1.0. x</span><span class="sxs-lookup"><span data-stu-id="e7b97-101">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>

<span data-ttu-id="e7b97-102">Rozhraní .NET Core pro Linux, které funguje v různých distribucích systému Linux, může podporovat OpenSSL 1.0. x i OpenSSL 1.1. x.</span><span class="sxs-lookup"><span data-stu-id="e7b97-102">.NET Core for Linux, which works across multiple Linux distributions, can support both OpenSSL 1.0.x and OpenSSL 1.1.x.</span></span>  <span data-ttu-id="e7b97-103">.NET Core 2,1 a .NET Core 2,2 hledejte nejprve 1,0. x a potom se vraťte na verzi 1.1. x; .NET Core 3,0 nejprve vyhledá 1.1. x.</span><span class="sxs-lookup"><span data-stu-id="e7b97-103">.NET Core 2.1 and .NET Core 2.2 look for 1.0.x first, then fall back to 1.1.x; .NET Core 3.0 looks for 1.1.x first.</span></span> <span data-ttu-id="e7b97-104">Tato změna byla provedena za účelem přidání podpory pro nové kryptografické standardy.</span><span class="sxs-lookup"><span data-stu-id="e7b97-104">This change was made to add support for new cryptographic standards.</span></span>

<span data-ttu-id="e7b97-105">Tato změna může mít vliv na knihovny nebo aplikace, které podporují interoperabilitu platforem s typy spolupráce OpenSSL specifickými pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e7b97-105">This change may impact libraries or applications that do platform interop with the OpenSSL-specific interop types in .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e7b97-106">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="e7b97-106">Change description</span></span>

<span data-ttu-id="e7b97-107">V .NET Core 2,2 a starších verzích modul runtime upřednostňuje načítání OpenSSL 1.0. x přes 1.1. x.</span><span class="sxs-lookup"><span data-stu-id="e7b97-107">In .NET Core 2.2 and earlier versions, the runtime prefers loading OpenSSL 1.0.x over 1.1.x.</span></span> <span data-ttu-id="e7b97-108">To znamená, že <xref:System.IntPtr> typy <xref:System.Runtime.InteropServices.SafeHandle> a pro interoperabilitu s OpenSSL se používají s libcrypto. so. 1.0.0/libcrypto. so. 1,0/libcrypto. so. 10 Podle preference.</span><span class="sxs-lookup"><span data-stu-id="e7b97-108">This means that the <xref:System.IntPtr> and <xref:System.Runtime.InteropServices.SafeHandle> types for interop with OpenSSL are used with libcrypto.so.1.0.0 / libcrypto.so.1.0 / libcrypto.so.10 by preference.</span></span>

<span data-ttu-id="e7b97-109">Počínaje rozhraním .NET Core 3,0, modul runtime upřednostňuje načtení OpenSSL 1.1. x nad OpenSSL 1.0. x, takže <xref:System.IntPtr> typy a <xref:System.Runtime.InteropServices.SafeHandle> pro spolupráci s OpenSSL se používají s libcrypto. proto. 1.1/libcrypto. so. 11/libcrypto. so. 1.1.0/libcrypto. předvoleb.</span><span class="sxs-lookup"><span data-stu-id="e7b97-109">Starting with .NET Core 3.0, the runtime prefers loading OpenSSL 1.1.x over OpenSSL 1.0.x, so the <xref:System.IntPtr> and <xref:System.Runtime.InteropServices.SafeHandle> types for interop with OpenSSL are used with libcrypto.so.1.1 / libcrypto.so.11 / libcrypto.so.1.1.0 / libcrypto.so.1.1.1 by preference.</span></span> <span data-ttu-id="e7b97-110">V důsledku toho můžou knihovny a aplikace, které spolupracují s OpenSSL, mít při upgradu z .NET Core 2,1 nebo .NET Core 2,2 nekompatibilní ukazatele s hodnotami vystavenými .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e7b97-110">As a result, libraries and applications that interoperate with OpenSSL directly may have incompatible pointers with the .NET Core-exposed values when upgrading from .NET Core 2.1 or .NET Core 2.2.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e7b97-111">Představená verze</span><span class="sxs-lookup"><span data-stu-id="e7b97-111">Version introduced</span></span>

<span data-ttu-id="e7b97-112">3.0</span><span class="sxs-lookup"><span data-stu-id="e7b97-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e7b97-113">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="e7b97-113">Recommended action</span></span>

<span data-ttu-id="e7b97-114">Knihovny a aplikace, které provádějí přímé operace s OpenSSL, musí být opatrní, aby používaly stejnou verzi OpenSSL jako modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e7b97-114">Libraries and applications that do direct operations with OpenSSL need to be careful to ensure they are using the same version of OpenSSL as the .NET Core runtime.</span></span>

<span data-ttu-id="e7b97-115">Všechny knihovny nebo aplikace, které <xref:System.IntPtr> používají <xref:System.Runtime.InteropServices.SafeHandle> nebo hodnoty z kryptografických typů .NET Core přímo s OpenSSL by měly porovnat verzi knihovny, kterou používá, s novou <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> vlastností, aby se zajistilo, že ukazatele jsou kompatibility.</span><span class="sxs-lookup"><span data-stu-id="e7b97-115">All libraries or applications that use <xref:System.IntPtr> or <xref:System.Runtime.InteropServices.SafeHandle> values from the .NET Core cryptographic types directly with OpenSSL should compare the version of the library they use with the new <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> property to ensure the pointers are compatible.</span></span>

#### <a name="category"></a><span data-ttu-id="e7b97-116">Kategorie</span><span class="sxs-lookup"><span data-stu-id="e7b97-116">Category</span></span>

<span data-ttu-id="e7b97-117">Kryptografick</span><span class="sxs-lookup"><span data-stu-id="e7b97-117">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e7b97-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="e7b97-118">Affected APIs</span></span>

- <xref:System.Security.Cryptography.SafeEvpPKeyHandle.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.IntPtr)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.IntPtr)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.IntPtr)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.IntPtr)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Handle?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Security.Cryptography.SafeEvpPKeyHandle.#ctor`
- `M:System.Security.Cryptography.RSAOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.RSAOpenSsl.#ctor(System.Security.Cryptography.SafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.RSAOpenSsl.DuplicateKeyHandle`
- `M:System.Security.Cryptography.DSAOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.DSAOpenSsl.#ctor(System.Security.Cryptography.SafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.DSAOpenSsl.DuplicateKeyHandle`
- `M:System.Security.Cryptography.ECDsaOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.ECDsaOpenSsl.#ctor(System.Security.CryptographySafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.ECDsaOpenSsl.DuplicateKeyHandle`
- `M:System.Security.Cryptography.ECDiffieHellmanOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.ECDiffieHellmanOpenSsl.#ctor(System.Security.Cryptography.SafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.ECDiffieHellmanOpenSsl.DuplicateKeyHandle`
- `P:System.Security.Cryptography.X509Certificates.X509Certificate.Handle`

-->