---
ms.openlocfilehash: 519de92ca4201d199941afe6382ddf9fc480fbbd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614524"
---
### <a name="servicebase-doesnt-propagate-onstart-exceptions"></a><span data-ttu-id="21f15-101">ServiceBase nešíří výjimky OnStart.</span><span class="sxs-lookup"><span data-stu-id="21f15-101">ServiceBase doesn't propagate OnStart exceptions</span></span>

#### <a name="details"></a><span data-ttu-id="21f15-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="21f15-102">Details</span></span>

<span data-ttu-id="21f15-103">V .NET Framework 4,7 a dřívějších verzích nejsou výjimky vyvolané při spuštění služby šířeny volajícímu <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="21f15-103">In the .NET Framework 4.7 and earlier versions, exceptions thrown on service startup are not propagated to the caller of <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>.</span></span><br/><span data-ttu-id="21f15-104">Počínaje aplikacemi, které cílí na .NET Framework 4.7.1, modul runtime šíří výjimky pro <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> služby, které se nedaří spustit.</span><span class="sxs-lookup"><span data-stu-id="21f15-104">Starting with applications that target the .NET Framework 4.7.1, the runtime propagates exceptions to <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> for services that fail to start.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="21f15-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="21f15-105">Suggestion</span></span>

<span data-ttu-id="21f15-106">Při spuštění služby, pokud dojde k výjimce, bude tato výjimka šířena.</span><span class="sxs-lookup"><span data-stu-id="21f15-106">On service start, if there is an exception, that exception will be propagated.</span></span> <span data-ttu-id="21f15-107">To by mělo pomáhat diagnostikovat případy, kdy se služby nedaří spustit.</span><span class="sxs-lookup"><span data-stu-id="21f15-107">This should help diagnose cases where services fail to start.</span></span> <br/><span data-ttu-id="21f15-108">Pokud je toto chování nežádoucí, můžete si ho odhlásit přidáním následujícího &lt; &gt; elementu AppContextSwitchOverrides do &lt; &gt; oddílu runtime konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="21f15-108">If this behavior is undesirable, you can opt out of it by adding the following &lt;AppContextSwitchOverrides&gt; element to the &lt;runtime&gt; section of your application configuration file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.ServiceProcess.DontThrowExceptionsOnStart=true" />
```

<span data-ttu-id="21f15-109">Pokud je vaše aplikace cílena na starší verzi než 4.7.1, ale chcete mít toto chování, přidejte následující &lt; &gt; element AppContextSwitchOverrides do &lt; oddílu runtime &gt; konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="21f15-109">If your application targets an earlier version than 4.7.1 but you want to have this behavior, add the following &lt;AppContextSwitchOverrides&gt; element to the &lt;runtime&gt; section of your application configuration file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.ServiceProcess.DontThrowExceptionsOnStart=false" />
```

| <span data-ttu-id="21f15-110">Name</span><span class="sxs-lookup"><span data-stu-id="21f15-110">Name</span></span>    | <span data-ttu-id="21f15-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="21f15-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="21f15-112">Rozsah</span><span class="sxs-lookup"><span data-stu-id="21f15-112">Scope</span></span>   | <span data-ttu-id="21f15-113">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="21f15-113">Minor</span></span>       |
| <span data-ttu-id="21f15-114">Verze</span><span class="sxs-lookup"><span data-stu-id="21f15-114">Version</span></span> | <span data-ttu-id="21f15-115">4.7.1</span><span class="sxs-lookup"><span data-stu-id="21f15-115">4.7.1</span></span>       |
| <span data-ttu-id="21f15-116">Typ</span><span class="sxs-lookup"><span data-stu-id="21f15-116">Type</span></span>    | <span data-ttu-id="21f15-117">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="21f15-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="21f15-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="21f15-118">Affected APIs</span></span>

- <xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase)?displayProperty=nameWithType>
- <xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase[])?displayProperty=nameWithType>
