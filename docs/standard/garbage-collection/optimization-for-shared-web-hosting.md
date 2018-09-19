---
title: Optimalizace pro sdílené hostování webů
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7831e383a3048523909b79ac5a4706f3c1c48371
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46004865"
---
# <a name="optimization-for-shared-web-hosting"></a><span data-ttu-id="950b3-102">Optimalizace pro sdílené hostování webů</span><span class="sxs-lookup"><span data-stu-id="950b3-102">Optimization for Shared Web Hosting</span></span>
<span data-ttu-id="950b3-103">Pokud jste správce pro server, které jsou sdíleny několika malými weby hostování, můžete optimalizovat výkon a zvýšit kapacitu webu přidáním následujícího kódu `gcTrimCommitOnLowMemory` nastavení `runtime` uzlu v souboru Aspnet.config v rozhraní .NET adresář:</span><span class="sxs-lookup"><span data-stu-id="950b3-103">If you are the administrator for a server that is shared by hosting several small Web sites, you can optimize performance and increase site capacity by adding the following `gcTrimCommitOnLowMemory` setting to the `runtime` node in the Aspnet.config file in the .NET directory:</span></span>  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
>  <span data-ttu-id="950b3-104">Toto nastavení se doporučuje jenom pro sdílený Web scénářích hostování.</span><span class="sxs-lookup"><span data-stu-id="950b3-104">This setting is recommended only for shared Web hosting scenarios.</span></span>  
  
 <span data-ttu-id="950b3-105">Vzhledem k tomu, že systému uvolňování paměti zachová pro budoucí přidělení paměti, lze jeho potvrzeného místa více než je nezbytně nutné.</span><span class="sxs-lookup"><span data-stu-id="950b3-105">Because the garbage collector retains memory for future allocations, its committed space can be more than what is strictly needed.</span></span> <span data-ttu-id="950b3-106">Můžete snížit toto místo tak, aby vyhovovaly dobu při velkém zatížení na systémové paměti.</span><span class="sxs-lookup"><span data-stu-id="950b3-106">You can reduce this space to accommodate times when there is a heavy load on system memory.</span></span> <span data-ttu-id="950b3-107">Zmenšení potvrzené zlepšuje výkon a rozbalí kapacitu pro hostování více webů.</span><span class="sxs-lookup"><span data-stu-id="950b3-107">Reducing this committed space improves performance and expands the capacity to host more sites.</span></span>  
  
 <span data-ttu-id="950b3-108">Když `gcTrimCommitOnLowMemory` nastavení povolené, vyhodnotí zatížení paměti systému uvolňování paměti a přejde do režimu ořezávání, když zatížení dosáhne 90 %.</span><span class="sxs-lookup"><span data-stu-id="950b3-108">When the `gcTrimCommitOnLowMemory` setting is enabled, the garbage collector evaluates the system memory load and enters a trimming mode when the load reaches 90%.</span></span> <span data-ttu-id="950b3-109">Udržuje oříznutí režimu, dokud se zatížení sníží pod 85 %.</span><span class="sxs-lookup"><span data-stu-id="950b3-109">It maintains the trimming mode until the load drops under 85%.</span></span>  
  
 <span data-ttu-id="950b3-110">Při povolení podmínky systému uvolňování paměti může rozhodnout, že `gcTrimCommitOnLowMemory` nastavení nebude nápověda aktuální aplikace a ho ignorovat.</span><span class="sxs-lookup"><span data-stu-id="950b3-110">When conditions permit, the garbage collector can decide that the `gcTrimCommitOnLowMemory` setting will not help the current application and ignore it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="950b3-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="950b3-111">Example</span></span>  
 <span data-ttu-id="950b3-112">Následující fragment XML ukazuje, jak povolit `gcTrimCommitOnLowMemory` nastavení.</span><span class="sxs-lookup"><span data-stu-id="950b3-112">The following XML fragment shows how to enable the `gcTrimCommitOnLowMemory` setting.</span></span> <span data-ttu-id="950b3-113">Symbol tří teček označuje další nastavení, která by byla `runtime` uzlu.</span><span class="sxs-lookup"><span data-stu-id="950b3-113">Ellipses indicate other settings that would be in the `runtime` node.</span></span>  
  
```xml  
<?xml version="1.0" encoding="UTF-8"?>  
<configuration>  
    <runtime>  
    . . .  
    <gcTrimCommitOnLowMemory enabled="true"/>  
    </runtime>  
    . . .  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="950b3-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="950b3-114">See also</span></span>

- [<span data-ttu-id="950b3-115">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="950b3-115">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
