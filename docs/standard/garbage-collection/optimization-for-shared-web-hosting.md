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
ms.openlocfilehash: c3c979477f0928c9c3d2a393042867c84df33ecf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571966"
---
# <a name="optimization-for-shared-web-hosting"></a><span data-ttu-id="80bf1-102">Optimalizace pro sdílené hostování webů</span><span class="sxs-lookup"><span data-stu-id="80bf1-102">Optimization for Shared Web Hosting</span></span>
<span data-ttu-id="80bf1-103">Pokud jste správce pro server, který je sdílen hostování několik malých webových serverů, můžete optimalizovat výkon a zvýšit kapacitu lokality přidáním následující `gcTrimCommitOnLowMemory` nastavení na `runtime` uzlu v souboru Aspnet.config v rozhraní .NET adresář:</span><span class="sxs-lookup"><span data-stu-id="80bf1-103">If you are the administrator for a server that is shared by hosting several small Web sites, you can optimize performance and increase site capacity by adding the following `gcTrimCommitOnLowMemory` setting to the `runtime` node in the Aspnet.config file in the .NET directory:</span></span>  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
>  <span data-ttu-id="80bf1-104">Toto nastavení se doporučuje jenom pro sdílené webové hostování scénáře.</span><span class="sxs-lookup"><span data-stu-id="80bf1-104">This setting is recommended only for shared Web hosting scenarios.</span></span>  
  
 <span data-ttu-id="80bf1-105">Vzhledem k tomu, že zachová má systém uvolňování paměti pro budoucí přidělení, lze jeho potvrdit místo více než je nezbytně nutné.</span><span class="sxs-lookup"><span data-stu-id="80bf1-105">Because the garbage collector retains memory for future allocations, its committed space can be more than what is strictly needed.</span></span> <span data-ttu-id="80bf1-106">Tento prostor, aby pojmulo doby můžete snížit při velkém zatížení na systémové paměti.</span><span class="sxs-lookup"><span data-stu-id="80bf1-106">You can reduce this space to accommodate times when there is a heavy load on system memory.</span></span> <span data-ttu-id="80bf1-107">Zmenšení potvrdit vylepšuje výkon a rozbalí kapacitu pro hostování více webů.</span><span class="sxs-lookup"><span data-stu-id="80bf1-107">Reducing this committed space improves performance and expands the capacity to host more sites.</span></span>  
  
 <span data-ttu-id="80bf1-108">Když `gcTrimCommitOnLowMemory` je povolené nastavení, vyhodnotí zatížení paměti systému uvolňování paměti a vstupuje do režimu oříznutí, pokud zatížení dosáhne 90 %.</span><span class="sxs-lookup"><span data-stu-id="80bf1-108">When the `gcTrimCommitOnLowMemory` setting is enabled, the garbage collector evaluates the system memory load and enters a trimming mode when the load reaches 90%.</span></span> <span data-ttu-id="80bf1-109">Dokud zatížení klesne pod položkou 85 % udržuje režimu oříznutí.</span><span class="sxs-lookup"><span data-stu-id="80bf1-109">It maintains the trimming mode until the load drops under 85%.</span></span>  
  
 <span data-ttu-id="80bf1-110">Když podmínky povolit, bude systém uvolňování můžete rozhodnout, že `gcTrimCommitOnLowMemory` nastavení nebude pomůže aktuální aplikace a ho ignorovat.</span><span class="sxs-lookup"><span data-stu-id="80bf1-110">When conditions permit, the garbage collector can decide that the `gcTrimCommitOnLowMemory` setting will not help the current application and ignore it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80bf1-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="80bf1-111">Example</span></span>  
 <span data-ttu-id="80bf1-112">Následující fragment kódu XML ukazuje, jak povolit `gcTrimCommitOnLowMemory` nastavení.</span><span class="sxs-lookup"><span data-stu-id="80bf1-112">The following XML fragment shows how to enable the `gcTrimCommitOnLowMemory` setting.</span></span> <span data-ttu-id="80bf1-113">Tři tečky znamenat další nastavení, které by se v `runtime` uzlu.</span><span class="sxs-lookup"><span data-stu-id="80bf1-113">Ellipses indicate other settings that would be in the `runtime` node.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="80bf1-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="80bf1-114">See Also</span></span>  
 [<span data-ttu-id="80bf1-115">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="80bf1-115">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
