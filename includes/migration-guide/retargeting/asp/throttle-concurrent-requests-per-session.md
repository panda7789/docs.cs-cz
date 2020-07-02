---
ms.openlocfilehash: b521f4163bf5bf4a369d0eec12dae503703a976e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614436"
---
### <a name="throttle-concurrent-requests-per-session"></a><span data-ttu-id="4ac79-101">Omezit souběžné požadavky na relaci</span><span class="sxs-lookup"><span data-stu-id="4ac79-101">Throttle concurrent requests per session</span></span>

#### <a name="details"></a><span data-ttu-id="4ac79-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="4ac79-102">Details</span></span>

<span data-ttu-id="4ac79-103">V .NET Framework 4.6.2 a dříve ASP.NET spouští požadavky se stejným identifikátorem SessionID sekvenčně a ASP.NET vždy vystavuje identifikátor SessionID prostřednictvím souborů cookie ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="4ac79-103">In the .NET Framework 4.6.2 and earlier, ASP.NET executes requests with the same Sessionid sequentially, and ASP.NET always issues the Sessionid through cookies by default.</span></span> <span data-ttu-id="4ac79-104">Pokud bude odpověď trvat dlouhou dobu, významně sníží výkon serveru pouhým stisknutím klávesy <kbd>F5</kbd> v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="4ac79-104">If a page takes a long time to respond, it will significantly degrade server performance just by pressing <kbd>F5</kbd> on the browser.</span></span> <span data-ttu-id="4ac79-105">V této opravě jsme přidali čítač, který sleduje požadavky ve frontě a ukončí žádosti, když překročí zadaný limit.</span><span class="sxs-lookup"><span data-stu-id="4ac79-105">In the fix, we added a counter to track the queued requests and terminate the requests when they exceed a specified limit.</span></span> <span data-ttu-id="4ac79-106">Výchozí hodnota je 50.</span><span class="sxs-lookup"><span data-stu-id="4ac79-106">The default value is 50.</span></span> <span data-ttu-id="4ac79-107">Pokud je dosaženo limitu, bude zaznamenáno upozornění v protokolu událostí a odpověď HTTP 500 může být zaznamenána v protokolu služby IIS.</span><span class="sxs-lookup"><span data-stu-id="4ac79-107">If the limit is reached, a warning will be logged in the event log, and an HTTP 500 response may be recorded in the IIS log.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4ac79-108">Návrh</span><span class="sxs-lookup"><span data-stu-id="4ac79-108">Suggestion</span></span>

<span data-ttu-id="4ac79-109">Chcete-li obnovit původní chování, můžete do souboru web.config přidat následující nastavení, abyste se odhlásili od nového chování.</span><span class="sxs-lookup"><span data-stu-id="4ac79-109">To restore the old behavior, you can add the following setting to your web.config file to opt out of the new behavior.</span></span>

```xml
<appSettings>
    <add key="aspnet:RequestQueueLimitPerSession" value="2147483647"/>
</appSettings>
```

| <span data-ttu-id="4ac79-110">Name</span><span class="sxs-lookup"><span data-stu-id="4ac79-110">Name</span></span>    | <span data-ttu-id="4ac79-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="4ac79-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4ac79-112">Rozsah</span><span class="sxs-lookup"><span data-stu-id="4ac79-112">Scope</span></span>   | <span data-ttu-id="4ac79-113">Edge</span><span class="sxs-lookup"><span data-stu-id="4ac79-113">Edge</span></span>        |
| <span data-ttu-id="4ac79-114">Verze</span><span class="sxs-lookup"><span data-stu-id="4ac79-114">Version</span></span> | <span data-ttu-id="4ac79-115">4,7</span><span class="sxs-lookup"><span data-stu-id="4ac79-115">4.7</span></span>         |
| <span data-ttu-id="4ac79-116">Typ</span><span class="sxs-lookup"><span data-stu-id="4ac79-116">Type</span></span>    | <span data-ttu-id="4ac79-117">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="4ac79-117">Retargeting</span></span> |
