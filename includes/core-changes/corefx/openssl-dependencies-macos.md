---
ms.openlocfilehash: a4476fbff572c004632153e5a98812c241efca57
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720897"
---
### <a name="openssl-versions-on-macos"></a><span data-ttu-id="784f5-101">Verze OpenSSL v macOS</span><span class="sxs-lookup"><span data-stu-id="784f5-101">OpenSSL versions on macOS</span></span>

<span data-ttu-id="784f5-102">Moduly runtime .NET Core 3,0 a novější v MacOS nyní upřednostňují OpenSSL verze 1.1. x pro OpenSSL 1.0. x pro <xref:System.Security.Cryptography.AesCcm> typy,,, <xref:System.Security.Cryptography.AesGcm> <xref:System.Security.Cryptography.DSAOpenSsl> <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> , <xref:System.Security.Cryptography.ECDsaOpenSsl> , <xref:System.Security.Cryptography.RSAOpenSsl> a <xref:System.Security.Cryptography.SafeEvpPKeyHandle> .</span><span class="sxs-lookup"><span data-stu-id="784f5-102">The .NET Core 3.0 and later runtimes on macOS now prefer OpenSSL 1.1.x versions to OpenSSL 1.0.x versions for the <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl>, and <xref:System.Security.Cryptography.SafeEvpPKeyHandle> types.</span></span>

<span data-ttu-id="784f5-103">Modul runtime .NET Core 2,1 teď podporuje verze OpenSSL 1.1. x, ale přesto upřednostňuje verze OpenSSL 1.0. x.</span><span class="sxs-lookup"><span data-stu-id="784f5-103">The .NET Core 2.1 runtime now supports OpenSSL 1.1.x versions, but still prefers OpenSSL 1.0.x versions.</span></span>

#### <a name="change-description"></a><span data-ttu-id="784f5-104">Popis změny</span><span class="sxs-lookup"><span data-stu-id="784f5-104">Change description</span></span>

<span data-ttu-id="784f5-105">V minulosti používal modul runtime .NET Core OpenSSL verze 1.0. x v macOS pro typy, které komunikují s OpenSSL.</span><span class="sxs-lookup"><span data-stu-id="784f5-105">Previously, the .NET Core runtime used OpenSSL 1.0.x versions on macOS for types that interact with OpenSSL.</span></span> <span data-ttu-id="784f5-106">Nejnovější verze OpenSSL 1.0. x, OpenSSL 1.0.2, teď není podporovaná.</span><span class="sxs-lookup"><span data-stu-id="784f5-106">The most recent OpenSSL 1.0.x version, OpenSSL 1.0.2, is now out of support.</span></span> <span data-ttu-id="784f5-107">Chcete-li zachovat typy, které používají OpenSSL na podporovaných verzích OpenSSL, rozhraní .NET Core 3,0 a novější modul runtime nyní používají novější verze OpenSSL v macOS.</span><span class="sxs-lookup"><span data-stu-id="784f5-107">To keep types that use OpenSSL on supported versions of OpenSSL, the .NET Core 3.0 and later runtimes now use newer versions of OpenSSL on macOS.</span></span>

<span data-ttu-id="784f5-108">Tato změna znamená, že chování pro modul runtime .NET Core v macOS je následující:</span><span class="sxs-lookup"><span data-stu-id="784f5-108">With this change, the behavior for the .NET Core runtimes on macOS is as follows:</span></span>

- <span data-ttu-id="784f5-109">Modul runtime .NET Core 3,0 a novější verze používá OpenSSL 1.1. x, pokud je k dispozici, a vraťte se do OpenSSL 1.0. x, pouze pokud není k dispozici žádná verze 1.1. x.</span><span class="sxs-lookup"><span data-stu-id="784f5-109">The .NET Core 3.0 and later version runtimes use OpenSSL 1.1.x, if available, and fall back to OpenSSL 1.0.x only if there's no 1.1.x version available.</span></span>

  <span data-ttu-id="784f5-110">Pro volající, kteří používají typy spolupráce OpenSSL s vlastními P/Invoke, postupujte podle pokynů v <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> komentářích.</span><span class="sxs-lookup"><span data-stu-id="784f5-110">For callers that use the OpenSSL interop types with custom P/Invokes, follow the guidance in the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> remarks.</span></span> <span data-ttu-id="784f5-111">Vaše aplikace může selhat, pokud hodnotu nekontrolujete <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> .</span><span class="sxs-lookup"><span data-stu-id="784f5-111">Your app may crash if you don't check the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> value.</span></span>

- <span data-ttu-id="784f5-112">Modul runtime .NET Core 2,1 používá OpenSSL 1.0. x, pokud je k dispozici, a vrátí se k OpenSSL 1.1. x, pokud není k dispozici žádná verze 1.0. x.</span><span class="sxs-lookup"><span data-stu-id="784f5-112">The .NET Core 2.1 runtime uses OpenSSL 1.0.x, if available, and falls back to OpenSSL 1.1.x if there's no 1.0.x version available.</span></span>

  <span data-ttu-id="784f5-113">Modul runtime 2,1 preferuje starší verzi OpenSSL <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> , protože vlastnost v rozhraní .NET Core 2,1 neexistuje, takže verzi OpenSSL nelze spolehlivě určit v době běhu.</span><span class="sxs-lookup"><span data-stu-id="784f5-113">The 2.1 runtime prefers the earlier version of OpenSSL because the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> property does not exist in .NET Core 2.1, so the OpenSSL version cannot be reliably determined at run time.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="784f5-114">Představená verze</span><span class="sxs-lookup"><span data-stu-id="784f5-114">Version introduced</span></span>

- <span data-ttu-id="784f5-115">.NET Core 2.1.16</span><span class="sxs-lookup"><span data-stu-id="784f5-115">.NET Core 2.1.16</span></span>
- <span data-ttu-id="784f5-116">.NET Core 3.0.3</span><span class="sxs-lookup"><span data-stu-id="784f5-116">.NET Core 3.0.3</span></span>
- <span data-ttu-id="784f5-117">.NET Core 3.1.2</span><span class="sxs-lookup"><span data-stu-id="784f5-117">.NET Core 3.1.2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="784f5-118">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="784f5-118">Recommended action</span></span>

- <span data-ttu-id="784f5-119">Odinstalujte OpenSSL verze 1.0.2, pokud ji už nepotřebujete.</span><span class="sxs-lookup"><span data-stu-id="784f5-119">Uninstall OpenSSL version 1.0.2 if it's no longer needed.</span></span>

- <span data-ttu-id="784f5-120">Pokud používáte <xref:System.Security.Cryptography.AesCcm> <xref:System.Security.Cryptography.AesGcm> typy,, <xref:System.Security.Cryptography.DSAOpenSsl> ,, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl> , <xref:System.Security.Cryptography.RSAOpenSsl> nebo <xref:System.Security.Cryptography.SafeEvpPKeyHandle> , nainstalujte OpenSSL 1.1. x.</span><span class="sxs-lookup"><span data-stu-id="784f5-120">Install OpenSSL 1.1.x if you use the <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl>, or <xref:System.Security.Cryptography.SafeEvpPKeyHandle> types.</span></span>

- <span data-ttu-id="784f5-121">Pokud používáte typy spolupráce OpenSSL s vlastními P/Invoke, postupujte podle pokynů v <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> komentářích.</span><span class="sxs-lookup"><span data-stu-id="784f5-121">If you use the OpenSSL interop types with custom P/Invokes, follow the guidance in the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> remarks.</span></span>

#### <a name="category"></a><span data-ttu-id="784f5-122">Kategorie</span><span class="sxs-lookup"><span data-stu-id="784f5-122">Category</span></span>

<span data-ttu-id="784f5-123">Knihovny Core .NET</span><span class="sxs-lookup"><span data-stu-id="784f5-123">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="784f5-124">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="784f5-124">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AesCcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.AesGcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.SafeEvpPKeyHandle?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Security.Cryptography.AesCcm``
- `T:System.Security.Cryptography.AesGcm`
- `T:System.Security.Cryptography.DSAOpenSsl`
- `T:System.Security.Cryptography.ECDiffieHellmanOpenSsl`
- `T:System.Security.Cryptography.ECDsaOpenSsl`
- `T:System.Security.Cryptography.RSAOpenSsl`
- `T:System.Security.Cryptography.SafeEvpPKeyHandle`

-->
