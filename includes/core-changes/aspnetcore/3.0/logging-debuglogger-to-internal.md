---
ms.openlocfilehash: 958dede03e1c15f69f4ee676f13713ff43c29e96
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394109"
---
### <a name="logging-debuglogger-class-made-internal"></a><span data-ttu-id="d0dcf-101">Protokolování: Třída DebugLogger byla interní</span><span class="sxs-lookup"><span data-stu-id="d0dcf-101">Logging: DebugLogger class made internal</span></span>

<span data-ttu-id="d0dcf-102">Před ASP.NET Core 3.0 byl `DebugLogger` `public`modifikátor přístupu společnosti .</span><span class="sxs-lookup"><span data-stu-id="d0dcf-102">Prior to ASP.NET Core 3.0, `DebugLogger`'s access modifier was `public`.</span></span> <span data-ttu-id="d0dcf-103">V ASP.NET Core 3.0 se modifikátor přístupu změnil na `internal`.</span><span class="sxs-lookup"><span data-stu-id="d0dcf-103">In ASP.NET Core 3.0, the access modifier changed to `internal`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d0dcf-104">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="d0dcf-104">Version introduced</span></span>

<span data-ttu-id="d0dcf-105">3.0</span><span class="sxs-lookup"><span data-stu-id="d0dcf-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d0dcf-106">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="d0dcf-106">Reason for change</span></span>

<span data-ttu-id="d0dcf-107">Změna se provádí takto:</span><span class="sxs-lookup"><span data-stu-id="d0dcf-107">The change is being made to:</span></span>

* <span data-ttu-id="d0dcf-108">Vynutit konzistenci s `ConsoleLogger`jinými implementacemi protokolování, jako je například .</span><span class="sxs-lookup"><span data-stu-id="d0dcf-108">Enforce consistency with other logger implementations such as `ConsoleLogger`.</span></span>
* <span data-ttu-id="d0dcf-109">Zmenšete povrch rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="d0dcf-109">Reduce the API surface.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d0dcf-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="d0dcf-110">Recommended action</span></span>

<span data-ttu-id="d0dcf-111"><xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` Pomocí metody rozšíření povolte protokolování ladění.</span><span class="sxs-lookup"><span data-stu-id="d0dcf-111">Use the <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` extension method to enable debug logging.</span></span> <span data-ttu-id="d0dcf-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider>je také `public` stále v případě, že služba musí být registrována ručně.</span><span class="sxs-lookup"><span data-stu-id="d0dcf-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> is also still `public` in the event the service needs to be registered manually.</span></span>

#### <a name="category"></a><span data-ttu-id="d0dcf-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="d0dcf-113">Category</span></span>

<span data-ttu-id="d0dcf-114">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d0dcf-114">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d0dcf-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="d0dcf-115">Affected APIs</span></span>

<xref:Microsoft.Extensions.Logging.Debug.DebugLogger?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.Extensions.Logging.Debug.DebugLogger`

-->
