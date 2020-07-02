---
ms.openlocfilehash: 87dc93ece10eaedbfbabddb5f857d0bcd12e05c4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615692"
---
### <a name="only-tls-10-11-and-12-protocols-supported-in-systemnetservicepointmanager-and-systemnetsecuritysslstream"></a><span data-ttu-id="37cf1-101">V System .NET. Třída ServicePointManager a System .NET. Security. SslStream se podporují jenom protokoly TLS 1,0, 1,1 a 1,2.</span><span class="sxs-lookup"><span data-stu-id="37cf1-101">Only Tls 1.0, 1.1 and 1.2 protocols supported in System.Net.ServicePointManager and System.Net.Security.SslStream</span></span>

#### <a name="details"></a><span data-ttu-id="37cf1-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="37cf1-102">Details</span></span>

<span data-ttu-id="37cf1-103">Počínaje .NET Framework 4,6 <xref:System.Net.ServicePointManager> <xref:System.Net.Security.SslStream> jsou třídy a povoleny pouze pomocí jednoho z následujících tří protokolů: TLS 1.0, TLS 1.1 nebo TLS 1.2.</span><span class="sxs-lookup"><span data-stu-id="37cf1-103">Starting with the .NET Framework 4.6, the <xref:System.Net.ServicePointManager> and <xref:System.Net.Security.SslStream> classes are only allowed to use one of the following three protocols: Tls1.0, Tls1.1, or Tls1.2.</span></span> <span data-ttu-id="37cf1-104">Protokol SSL 3.0 a šifra šifry nejsou podporované.</span><span class="sxs-lookup"><span data-stu-id="37cf1-104">The SSL3.0 protocol and RC4 cipher are not supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="37cf1-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="37cf1-105">Suggestion</span></span>

<span data-ttu-id="37cf1-106">Doporučené zmírnění je upgrade aplikace na straně serveru na TLS 1.0, TLS 1.1 nebo TLS 1.2.</span><span class="sxs-lookup"><span data-stu-id="37cf1-106">The recommended mitigation is to upgrade the sever-side app to Tls1.0, Tls1.1, or Tls1.2.</span></span> <span data-ttu-id="37cf1-107">Pokud to není možné, nebo pokud jsou klientské aplikace poškozeny, <xref:System.AppContext?displayProperty=fullName> můžete tuto funkci použít k odhlášení z těchto funkcí jedním ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="37cf1-107">If this is not feasible, or if client apps are broken, the <xref:System.AppContext?displayProperty=fullName> class can be used to opt out of this feature in either of two ways:</span></span>

- <span data-ttu-id="37cf1-108">Programově nastavením kompatibilních přepínačů na <xref:System.AppContext?displayProperty=fullName> , jak je popsáno [zde](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</span><span class="sxs-lookup"><span data-stu-id="37cf1-108">By programmatically setting compat switches on the <xref:System.AppContext?displayProperty=fullName>, as explained [here](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</span></span>
- <span data-ttu-id="37cf1-109">Přidáním následujícího řádku do `<runtime>` části souboru app.config:</span><span class="sxs-lookup"><span data-stu-id="37cf1-109">By adding the following line to the `<runtime>` section of the app.config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>
```

| <span data-ttu-id="37cf1-110">Name</span><span class="sxs-lookup"><span data-stu-id="37cf1-110">Name</span></span>    | <span data-ttu-id="37cf1-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="37cf1-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="37cf1-112">Rozsah</span><span class="sxs-lookup"><span data-stu-id="37cf1-112">Scope</span></span>   | <span data-ttu-id="37cf1-113">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="37cf1-113">Minor</span></span>       |
| <span data-ttu-id="37cf1-114">Verze</span><span class="sxs-lookup"><span data-stu-id="37cf1-114">Version</span></span> | <span data-ttu-id="37cf1-115">4.6</span><span class="sxs-lookup"><span data-stu-id="37cf1-115">4.6</span></span>         |
| <span data-ttu-id="37cf1-116">Typ</span><span class="sxs-lookup"><span data-stu-id="37cf1-116">Type</span></span>    | <span data-ttu-id="37cf1-117">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="37cf1-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="37cf1-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="37cf1-118">Affected APIs</span></span>

- <xref:System.Net.SecurityProtocolType.Ssl3?displayProperty=nameWithType>
- <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>
- <xref:System.Security.Authentication.SslProtocols.Ssl2?displayProperty=nameWithType>
- <xref:System.Security.Authentication.SslProtocols.Ssl3?displayProperty=nameWithType>
