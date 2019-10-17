---
ms.openlocfilehash: 958dede03e1c15f69f4ee676f13713ff43c29e96
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394109"
---
### <a name="logging-debuglogger-class-made-internal"></a><span data-ttu-id="39f3e-101">Protokolování: DebugLogger třída provedla interní</span><span class="sxs-lookup"><span data-stu-id="39f3e-101">Logging: DebugLogger class made internal</span></span>

<span data-ttu-id="39f3e-102">Před ASP.NET Core 3,0 byl modifikátor přístupu `DebugLogger` `public`.</span><span class="sxs-lookup"><span data-stu-id="39f3e-102">Prior to ASP.NET Core 3.0, `DebugLogger`'s access modifier was `public`.</span></span> <span data-ttu-id="39f3e-103">V ASP.NET Core 3,0 se modifikátor přístupu změnil na `internal`.</span><span class="sxs-lookup"><span data-stu-id="39f3e-103">In ASP.NET Core 3.0, the access modifier changed to `internal`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="39f3e-104">Představená verze</span><span class="sxs-lookup"><span data-stu-id="39f3e-104">Version introduced</span></span>

<span data-ttu-id="39f3e-105">3.0</span><span class="sxs-lookup"><span data-stu-id="39f3e-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="39f3e-106">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="39f3e-106">Reason for change</span></span>

<span data-ttu-id="39f3e-107">Změna je provedena na:</span><span class="sxs-lookup"><span data-stu-id="39f3e-107">The change is being made to:</span></span>

* <span data-ttu-id="39f3e-108">Vyvynuťte konzistenci s jinými implementacemi protokolovacího nástroje, jako je například `ConsoleLogger`.</span><span class="sxs-lookup"><span data-stu-id="39f3e-108">Enforce consistency with other logger implementations such as `ConsoleLogger`.</span></span>
* <span data-ttu-id="39f3e-109">Snižte plochu rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="39f3e-109">Reduce the API surface.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="39f3e-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="39f3e-110">Recommended action</span></span>

<span data-ttu-id="39f3e-111">K povolení protokolování ladění použijte metodu rozšíření <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder`.</span><span class="sxs-lookup"><span data-stu-id="39f3e-111">Use the <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` extension method to enable debug logging.</span></span> <span data-ttu-id="39f3e-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> stále v případě, že je nutné zaregistrovat službu ručně, `public`.</span><span class="sxs-lookup"><span data-stu-id="39f3e-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> is also still `public` in the event the service needs to be registered manually.</span></span>

#### <a name="category"></a><span data-ttu-id="39f3e-113">Kategorie</span><span class="sxs-lookup"><span data-stu-id="39f3e-113">Category</span></span>

<span data-ttu-id="39f3e-114">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="39f3e-114">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="39f3e-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="39f3e-115">Affected APIs</span></span>

<xref:Microsoft.Extensions.Logging.Debug.DebugLogger?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.Extensions.Logging.Debug.DebugLogger`

-->
