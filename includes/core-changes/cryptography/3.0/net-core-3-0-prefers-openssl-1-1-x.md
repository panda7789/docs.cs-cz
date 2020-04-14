---
ms.openlocfilehash: 65d8ca480d41a3807473583355fe8be41e0e9701
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275176"
---
### <a name="net-core-30-prefers-openssl-11x-to-openssl-10x"></a><span data-ttu-id="77143-101">.NET Core 3.0 preferuje OpenSSL 1.1.x na OpenSSL 1.0.x</span><span class="sxs-lookup"><span data-stu-id="77143-101">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>

<span data-ttu-id="77143-102">.NET Core pro Linux, který funguje napříč několika linuxovými distribucemi, může podporovat jak OpenSSL 1.0.x, tak OpenSSL 1.1.x.</span><span class="sxs-lookup"><span data-stu-id="77143-102">.NET Core for Linux, which works across multiple Linux distributions, can support both OpenSSL 1.0.x and OpenSSL 1.1.x.</span></span>  <span data-ttu-id="77143-103">.NET Core 2.1 a .NET Core 2.2 nejprve hledají 1.0.x, pak se vrátí na 1.1.x; .NET Core 3.0 hledá nejprve 1.1.x.</span><span class="sxs-lookup"><span data-stu-id="77143-103">.NET Core 2.1 and .NET Core 2.2 look for 1.0.x first, then fall back to 1.1.x; .NET Core 3.0 looks for 1.1.x first.</span></span> <span data-ttu-id="77143-104">Tato změna byla provedena přidat podporu pro nové kryptografické standardy.</span><span class="sxs-lookup"><span data-stu-id="77143-104">This change was made to add support for new cryptographic standards.</span></span>

<span data-ttu-id="77143-105">Tato změna může mít vliv na knihovny nebo aplikace, které interop platformy s typy interop specifické pro OpenSSL v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="77143-105">This change may impact libraries or applications that do platform interop with the OpenSSL-specific interop types in .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="77143-106">Popis změny</span><span class="sxs-lookup"><span data-stu-id="77143-106">Change description</span></span>

<span data-ttu-id="77143-107">V rozhraní .NET Core 2.2 a starších verzích preferuje runtime načítání OpenSSL 1.0.x před 1.1.x.</span><span class="sxs-lookup"><span data-stu-id="77143-107">In .NET Core 2.2 and earlier versions, the runtime prefers loading OpenSSL 1.0.x over 1.1.x.</span></span> <span data-ttu-id="77143-108">To znamená, <xref:System.IntPtr> <xref:System.Runtime.InteropServices.SafeHandle> že typy a pro interop s OpenSSL se používají s libcrypto.so.1.0.0 / libcrypto.so.1.0 / libcrypto.so.10 podle preference.</span><span class="sxs-lookup"><span data-stu-id="77143-108">This means that the <xref:System.IntPtr> and <xref:System.Runtime.InteropServices.SafeHandle> types for interop with OpenSSL are used with libcrypto.so.1.0.0 / libcrypto.so.1.0 / libcrypto.so.10 by preference.</span></span>

<span data-ttu-id="77143-109">Počínaje .NET Core 3.0, runtime preferuje načítání OpenSSL 1.1.x přes OpenSSL <xref:System.IntPtr> 1.0.x, takže typy a <xref:System.Runtime.InteropServices.SafeHandle> pro interop s OpenSSL se používají s libcrypto.so.1.1 / libcrypto.so.11 / libcrypto.so.1.1.0 / libcrypto.so.1.1.1.</span><span class="sxs-lookup"><span data-stu-id="77143-109">Starting with .NET Core 3.0, the runtime prefers loading OpenSSL 1.1.x over OpenSSL 1.0.x, so the <xref:System.IntPtr> and <xref:System.Runtime.InteropServices.SafeHandle> types for interop with OpenSSL are used with libcrypto.so.1.1 / libcrypto.so.11 / libcrypto.so.1.1.0 / libcrypto.so.1.1.1 by preference.</span></span> <span data-ttu-id="77143-110">V důsledku toho mohou mít knihovny a aplikace, které přímo spolupracují s OpenSSL, nekompatibilní ukazatele s hodnotami vystavenými jádrem .NET při upgradu z rozhraní .NET Core 2.1 nebo .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="77143-110">As a result, libraries and applications that interoperate with OpenSSL directly may have incompatible pointers with the .NET Core-exposed values when upgrading from .NET Core 2.1 or .NET Core 2.2.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="77143-111">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="77143-111">Version introduced</span></span>

<span data-ttu-id="77143-112">3.0</span><span class="sxs-lookup"><span data-stu-id="77143-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="77143-113">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="77143-113">Recommended action</span></span>

<span data-ttu-id="77143-114">Knihovny a aplikace, které provádějí přímé operace s OpenSSL, musí být pečlivě nutné zajistit, aby používaly stejnou verzi OpenSSL jako zaběhu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="77143-114">Libraries and applications that do direct operations with OpenSSL need to be careful to ensure they are using the same version of OpenSSL as the .NET Core runtime.</span></span>

<span data-ttu-id="77143-115">Všechny knihovny nebo <xref:System.IntPtr> aplikace, které používají nebo <xref:System.Runtime.InteropServices.SafeHandle> hodnoty z kryptografických typů .NET Core přímo <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> s OpenSSL by měl porovnat verzi knihovny, které používají s novou vlastnost, aby bylo zajištěno, že ukazatele jsou kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="77143-115">All libraries or applications that use <xref:System.IntPtr> or <xref:System.Runtime.InteropServices.SafeHandle> values from the .NET Core cryptographic types directly with OpenSSL should compare the version of the library they use with the new <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> property to ensure the pointers are compatible.</span></span>

#### <a name="category"></a><span data-ttu-id="77143-116">Kategorie</span><span class="sxs-lookup"><span data-stu-id="77143-116">Category</span></span>

<span data-ttu-id="77143-117">Kryptografie</span><span class="sxs-lookup"><span data-stu-id="77143-117">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="77143-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="77143-118">Affected APIs</span></span>

- <xref:System.Security.Cryptography.SafeEvpPKeyHandle.%23ctor%2A>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.RSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.DSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
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
