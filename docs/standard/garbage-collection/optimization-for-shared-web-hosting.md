---
title: Optimalizace pro sdílené hostování webů
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
ms.openlocfilehash: 07a100e2cd6aaff2b54b99144c9d762c8979fb47
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140268"
---
# <a name="optimization-for-shared-web-hosting"></a><span data-ttu-id="f0721-102">Optimalizace pro sdílené hostování webů</span><span class="sxs-lookup"><span data-stu-id="f0721-102">Optimization for Shared Web Hosting</span></span>
<span data-ttu-id="f0721-103">Pokud jste správcem serveru, který je sdílen hostováním několika malých webů, můžete `gcTrimCommitOnLowMemory` optimalizovat výkon `runtime` a zvýšit kapacitu webu přidáním následujícího nastavení do uzlu v souboru Aspnet.config v adresáři .NET:</span><span class="sxs-lookup"><span data-stu-id="f0721-103">If you are the administrator for a server that is shared by hosting several small Web sites, you can optimize performance and increase site capacity by adding the following `gcTrimCommitOnLowMemory` setting to the `runtime` node in the Aspnet.config file in the .NET directory:</span></span>  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
> <span data-ttu-id="f0721-104">Toto nastavení se doporučuje pouze pro scénáře sdíleného webhostingu.</span><span class="sxs-lookup"><span data-stu-id="f0721-104">This setting is recommended only for shared Web hosting scenarios.</span></span>  
  
 <span data-ttu-id="f0721-105">Vzhledem k tomu, že systém uvolňování paměti zachová paměť pro budoucí přidělení, jeho potvrzené místo může být více než to, co je nezbytně nutné.</span><span class="sxs-lookup"><span data-stu-id="f0721-105">Because the garbage collector retains memory for future allocations, its committed space can be more than what is strictly needed.</span></span> <span data-ttu-id="f0721-106">Tento prostor můžete zmenšit tak, aby vyhovoval času, kdy dochází k silnému zatížení systémové paměti.</span><span class="sxs-lookup"><span data-stu-id="f0721-106">You can reduce this space to accommodate times when there is a heavy load on system memory.</span></span> <span data-ttu-id="f0721-107">Snížení tohoto přiděleného prostoru zvyšuje výkon a rozšiřuje kapacitu pro hostování více webů.</span><span class="sxs-lookup"><span data-stu-id="f0721-107">Reducing this committed space improves performance and expands the capacity to host more sites.</span></span>  
  
 <span data-ttu-id="f0721-108">Pokud `gcTrimCommitOnLowMemory` je toto nastavení povoleno, systém uvolňování paměti vyhodnotí zatížení systémové paměti a přejde do režimu oříznutí, když zatížení dosáhne 90 %.</span><span class="sxs-lookup"><span data-stu-id="f0721-108">When the `gcTrimCommitOnLowMemory` setting is enabled, the garbage collector evaluates the system memory load and enters a trimming mode when the load reaches 90%.</span></span> <span data-ttu-id="f0721-109">Udržuje režim ořezávání, dokud zatížení neklesne pod 85%.</span><span class="sxs-lookup"><span data-stu-id="f0721-109">It maintains the trimming mode until the load drops under 85%.</span></span>  
  
 <span data-ttu-id="f0721-110">Pokud to podmínky dovolí, systém `gcTrimCommitOnLowMemory` uvolňování paměti může rozhodnout, že nastavení nepomůže aktuální aplikaci a ignoruje ji.</span><span class="sxs-lookup"><span data-stu-id="f0721-110">When conditions permit, the garbage collector can decide that the `gcTrimCommitOnLowMemory` setting will not help the current application and ignore it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0721-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="f0721-111">Example</span></span>  
 <span data-ttu-id="f0721-112">Následující fragment XML ukazuje, `gcTrimCommitOnLowMemory` jak povolit nastavení.</span><span class="sxs-lookup"><span data-stu-id="f0721-112">The following XML fragment shows how to enable the `gcTrimCommitOnLowMemory` setting.</span></span> <span data-ttu-id="f0721-113">Elipsy označují další nastavení, která `runtime` by byla v uzlu.</span><span class="sxs-lookup"><span data-stu-id="f0721-113">Ellipses indicate other settings that would be in the `runtime` node.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f0721-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="f0721-114">See also</span></span>

- [<span data-ttu-id="f0721-115">Kolekce paměti</span><span class="sxs-lookup"><span data-stu-id="f0721-115">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
