---
title: "Optimalizace pro sdílené hostování webů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1f423d867d4fada075800650627c94f9d09e9e7a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="optimization-for-shared-web-hosting"></a><span data-ttu-id="dd002-102">Optimalizace pro sdílené hostování webů</span><span class="sxs-lookup"><span data-stu-id="dd002-102">Optimization for Shared Web Hosting</span></span>
<span data-ttu-id="dd002-103">Pokud jste správce pro server, který je sdílen hostování několik malých webových serverů, můžete optimalizovat výkon a zvýšit kapacitu lokality přidáním následující `gcTrimCommitOnLowMemory` nastavení na `runtime` uzlu v souboru Aspnet.config v rozhraní .NET adresář:</span><span class="sxs-lookup"><span data-stu-id="dd002-103">If you are the administrator for a server that is shared by hosting several small Web sites, you can optimize performance and increase site capacity by adding the following `gcTrimCommitOnLowMemory` setting to the `runtime` node in the Aspnet.config file in the .NET directory:</span></span>  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
>  <span data-ttu-id="dd002-104">Toto nastavení se doporučuje jenom pro sdílené webové hostování scénáře.</span><span class="sxs-lookup"><span data-stu-id="dd002-104">This setting is recommended only for shared Web hosting scenarios.</span></span>  
  
 <span data-ttu-id="dd002-105">Vzhledem k tomu, že zachová má systém uvolňování paměti pro budoucí přidělení, lze jeho potvrdit místo více než je nezbytně nutné.</span><span class="sxs-lookup"><span data-stu-id="dd002-105">Because the garbage collector retains memory for future allocations, its committed space can be more than what is strictly needed.</span></span> <span data-ttu-id="dd002-106">Tento prostor, aby pojmulo doby můžete snížit při velkém zatížení na systémové paměti.</span><span class="sxs-lookup"><span data-stu-id="dd002-106">You can reduce this space to accommodate times when there is a heavy load on system memory.</span></span> <span data-ttu-id="dd002-107">Zmenšení potvrdit vylepšuje výkon a rozbalí kapacitu pro hostování více webů.</span><span class="sxs-lookup"><span data-stu-id="dd002-107">Reducing this committed space improves performance and expands the capacity to host more sites.</span></span>  
  
 <span data-ttu-id="dd002-108">Když `gcTrimCommitOnLowMemory` je povolené nastavení, vyhodnotí zatížení paměti systému uvolňování paměti a vstupuje do režimu oříznutí, pokud zatížení dosáhne 90 %.</span><span class="sxs-lookup"><span data-stu-id="dd002-108">When the `gcTrimCommitOnLowMemory` setting is enabled, the garbage collector evaluates the system memory load and enters a trimming mode when the load reaches 90%.</span></span> <span data-ttu-id="dd002-109">Dokud zatížení klesne pod položkou 85 % udržuje režimu oříznutí.</span><span class="sxs-lookup"><span data-stu-id="dd002-109">It maintains the trimming mode until the load drops under 85%.</span></span>  
  
 <span data-ttu-id="dd002-110">Když podmínky povolit, bude systém uvolňování můžete rozhodnout, že `gcTrimCommitOnLowMemory` nastavení nebude pomůže aktuální aplikace a ho ignorovat.</span><span class="sxs-lookup"><span data-stu-id="dd002-110">When conditions permit, the garbage collector can decide that the `gcTrimCommitOnLowMemory` setting will not help the current application and ignore it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd002-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="dd002-111">Example</span></span>  
 <span data-ttu-id="dd002-112">Následující fragment kódu XML ukazuje, jak povolit `gcTrimCommitOnLowMemory` nastavení.</span><span class="sxs-lookup"><span data-stu-id="dd002-112">The following XML fragment shows how to enable the `gcTrimCommitOnLowMemory` setting.</span></span> <span data-ttu-id="dd002-113">Tři tečky znamenat další nastavení, které by se v `runtime` uzlu.</span><span class="sxs-lookup"><span data-stu-id="dd002-113">Ellipses indicate other settings that would be in the `runtime` node.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dd002-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="dd002-114">See Also</span></span>  
 [<span data-ttu-id="dd002-115">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="dd002-115">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
