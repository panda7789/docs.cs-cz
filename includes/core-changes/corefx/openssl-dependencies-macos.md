---
ms.openlocfilehash: 8790637c31d503455eb8ba722cca827c2a24b7c9
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021444"
---
### <a name="openssl-versions-on-macos"></a><span data-ttu-id="98402-101">Verze OpenSSL v macOS</span><span class="sxs-lookup"><span data-stu-id="98402-101">OpenSSL versions on macOS</span></span>

<span data-ttu-id="98402-102">Rozhraní .NET Core 3.0 a novější runtimes v systému macOS nyní preferují verze OpenSSL 1.1.x <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl>před <xref:System.Security.Cryptography.RSAOpenSsl>verzemi OpenSSL 1.0.x <xref:System.Security.Cryptography.SafeEvpPKeyHandle> pro typy <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, , , , .</span><span class="sxs-lookup"><span data-stu-id="98402-102">The .NET Core 3.0 and later runtimes on macOS now prefer OpenSSL 1.1.x versions to OpenSSL 1.0.x versions for the <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl>, and <xref:System.Security.Cryptography.SafeEvpPKeyHandle> types.</span></span>

<span data-ttu-id="98402-103">Runtime .NET Core 2.1 nyní podporuje verze OpenSSL 1.1.x, ale stále preferuje verze OpenSSL 1.0.x.</span><span class="sxs-lookup"><span data-stu-id="98402-103">The .NET Core 2.1 runtime now supports OpenSSL 1.1.x versions, but still prefers OpenSSL 1.0.x versions.</span></span>

#### <a name="change-description"></a><span data-ttu-id="98402-104">Popis změny</span><span class="sxs-lookup"><span data-stu-id="98402-104">Change description</span></span>

<span data-ttu-id="98402-105">Dříve používal runtime .NET Core verze OpenSSL 1.0.x v systému macOS pro typy, které interagují s OpenSSL.</span><span class="sxs-lookup"><span data-stu-id="98402-105">Previously, the .NET Core runtime used OpenSSL 1.0.x versions on macOS for types that interact with OpenSSL.</span></span> <span data-ttu-id="98402-106">Nejnovější verze OpenSSL 1.0.x, OpenSSL 1.0.2, je nyní mimo podporu.</span><span class="sxs-lookup"><span data-stu-id="98402-106">The most recent OpenSSL 1.0.x version, OpenSSL 1.0.2, is now out of support.</span></span> <span data-ttu-id="98402-107">Chcete-li zachovat typy, které používají OpenSSL v podporovaných verzích OpenSSL, používají nyní moduly .NET Core 3.0 a novější moduly runtimes novější verze OpenSSL v systému macOS.</span><span class="sxs-lookup"><span data-stu-id="98402-107">To keep types that use OpenSSL on supported versions of OpenSSL, the .NET Core 3.0 and later runtimes now use newer versions of OpenSSL on macOS.</span></span>

<span data-ttu-id="98402-108">S touto změnou je chování pro běhové toruny jádra .NET v systému macOS následující:</span><span class="sxs-lookup"><span data-stu-id="98402-108">With this change, the behavior for the .NET Core runtimes on macOS is as follows:</span></span>

- <span data-ttu-id="98402-109">Za běhu .NET Core 3.0 a novější verze používají OpenSSL 1.1.x, pokud jsou k dispozici, a vrátí se zpět na OpenSSL 1.0.x pouze v případě, že není k dispozici verze 1.1.x.</span><span class="sxs-lookup"><span data-stu-id="98402-109">The .NET Core 3.0 and later version runtimes use OpenSSL 1.1.x, if available, and fall back to OpenSSL 1.0.x only if there's no 1.1.x version available.</span></span>

  <span data-ttu-id="98402-110">Pro volající, kteří používají OpenSSL interop typy s vlastní P/Invokes, postupujte podle pokynů v <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> poznámkách.</span><span class="sxs-lookup"><span data-stu-id="98402-110">For callers that use the OpenSSL interop types with custom P/Invokes, follow the guidance in the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> remarks.</span></span> <span data-ttu-id="98402-111">Pokud hodnotu nezkontrolujete, <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> může dojít k chybě aplikace.</span><span class="sxs-lookup"><span data-stu-id="98402-111">Your app may crash if you don't check the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> value.</span></span>

- <span data-ttu-id="98402-112">Runtime .NET Core 2.1 používá OpenSSL 1.0.x, pokud je k dispozici, a přejde zpět na OpenSSL 1.1.x, pokud není k dispozici verze 1.0.x.</span><span class="sxs-lookup"><span data-stu-id="98402-112">The .NET Core 2.1 runtime uses OpenSSL 1.0.x, if available, and falls back to OpenSSL 1.1.x if there's no 1.0.x version available.</span></span>

  <span data-ttu-id="98402-113">Runtime 2.1 preferuje starší verzi OpenSSL, <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> protože vlastnost neexistuje v rozhraní .NET Core 2.1, takže verzi OpenSSL nelze spolehlivě určit za běhu.</span><span class="sxs-lookup"><span data-stu-id="98402-113">The 2.1 runtime prefers the earlier version of OpenSSL because the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> property does not exist in .NET Core 2.1, so the OpenSSL version cannot be reliably determined at run time.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="98402-114">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="98402-114">Version introduced</span></span>

- <span data-ttu-id="98402-115">.NET Jádro 2.1.16</span><span class="sxs-lookup"><span data-stu-id="98402-115">.NET Core 2.1.16</span></span>
- <span data-ttu-id="98402-116">.NET Jádro 3.0.3</span><span class="sxs-lookup"><span data-stu-id="98402-116">.NET Core 3.0.3</span></span>
- <span data-ttu-id="98402-117">.NET Jádro 3.1.2</span><span class="sxs-lookup"><span data-stu-id="98402-117">.NET Core 3.1.2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="98402-118">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="98402-118">Recommended action</span></span>

- <span data-ttu-id="98402-119">Odinstalujte OpenSSL verze 1.0.2, pokud už není potřeba.</span><span class="sxs-lookup"><span data-stu-id="98402-119">Uninstall OpenSSL version 1.0.2 if it's no longer needed.</span></span>

- <span data-ttu-id="98402-120"><xref:System.Security.Cryptography.AesCcm>Pokud používáte typy , <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl> <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl> <xref:System.Security.Cryptography.RSAOpenSsl>, , nebo <xref:System.Security.Cryptography.SafeEvpPKeyHandle> nainstalujete soubor OpenSSL 1.1.x.</span><span class="sxs-lookup"><span data-stu-id="98402-120">Install OpenSSL 1.1.x if you use the <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl>, or <xref:System.Security.Cryptography.SafeEvpPKeyHandle> types.</span></span>

- <span data-ttu-id="98402-121">Pokud používáte OpenSSL interop typy s vlastní P/Invokes, postupujte podle pokynů v <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> poznámkách.</span><span class="sxs-lookup"><span data-stu-id="98402-121">If you use the OpenSSL interop types with custom P/Invokes, follow the guidance in the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> remarks.</span></span>

#### <a name="category"></a><span data-ttu-id="98402-122">Kategorie</span><span class="sxs-lookup"><span data-stu-id="98402-122">Category</span></span>

<span data-ttu-id="98402-123">Základní knihovny .NET</span><span class="sxs-lookup"><span data-stu-id="98402-123">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="98402-124">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="98402-124">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AesCcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.AesGcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.SafeEvpPKeyHandle?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Security.Cryptography.AesCcm``
- `T:System.Security.Cryptography.AesGcm`
- `T:System.Security.Cryptography.DSAOpenSsl`
- `T:System.Security.Cryptography.ECDiffieHellmanOpenSsl`
- `T:System.Security.Cryptography.ECDsaOpenSsl`
- `T:System.Security.Cryptography.RSAOpenSsl`
- `T:System.Security.Cryptography.SafeEvpPKeyHandle`

-->
