---
title: Optimalizace pro sdílené hostování webů
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
ms.openlocfilehash: ccaacd44f8aaed9c3178cb94f98b0f58d4d3c7d4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84285986"
---
# <a name="optimization-for-shared-web-hosting"></a><span data-ttu-id="6e983-102">Optimalizace pro sdílené hostování webů</span><span class="sxs-lookup"><span data-stu-id="6e983-102">Optimization for Shared Web Hosting</span></span>
<span data-ttu-id="6e983-103">Pokud jste správcem serveru, který je sdílen hostitelem několika malých webů, můžete optimalizovat výkon a zvýšit kapacitu webu přidáním následujícího `gcTrimCommitOnLowMemory` nastavení do `runtime` uzlu v souboru ASPNET. config v adresáři .NET:</span><span class="sxs-lookup"><span data-stu-id="6e983-103">If you are the administrator for a server that is shared by hosting several small Web sites, you can optimize performance and increase site capacity by adding the following `gcTrimCommitOnLowMemory` setting to the `runtime` node in the Aspnet.config file in the .NET directory:</span></span>  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
> <span data-ttu-id="6e983-104">Toto nastavení se doporučuje jenom pro scénáře sdíleného hostování webů.</span><span class="sxs-lookup"><span data-stu-id="6e983-104">This setting is recommended only for shared Web hosting scenarios.</span></span>  
  
 <span data-ttu-id="6e983-105">Vzhledem k tomu, že systém uvolňování paměti zachovává paměť pro budoucí přidělení, může být jeho přizpůsobený prostor větší, než kolik jich je naprosto potřeba.</span><span class="sxs-lookup"><span data-stu-id="6e983-105">Because the garbage collector retains memory for future allocations, its committed space can be more than what is strictly needed.</span></span> <span data-ttu-id="6e983-106">Tento prostor můžete omezit tak, aby odpovídal času, když dojde k velkému zatížení systémové paměti.</span><span class="sxs-lookup"><span data-stu-id="6e983-106">You can reduce this space to accommodate times when there is a heavy load on system memory.</span></span> <span data-ttu-id="6e983-107">Omezením tohoto potvrzeného místa se zlepší výkon a rozšíří se kapacita na hostování více lokalit.</span><span class="sxs-lookup"><span data-stu-id="6e983-107">Reducing this committed space improves performance and expands the capacity to host more sites.</span></span>  
  
 <span data-ttu-id="6e983-108">Když `gcTrimCommitOnLowMemory` je toto nastavení povoleno, systém uvolňování paměti vyhodnotí zatížení systémové paměti a přejde do režimu oříznutí, pokud zatížení dosáhne 90%.</span><span class="sxs-lookup"><span data-stu-id="6e983-108">When the `gcTrimCommitOnLowMemory` setting is enabled, the garbage collector evaluates the system memory load and enters a trimming mode when the load reaches 90%.</span></span> <span data-ttu-id="6e983-109">Udržuje režim ořezávání, dokud zatížení neklesne pod 85%.</span><span class="sxs-lookup"><span data-stu-id="6e983-109">It maintains the trimming mode until the load drops under 85%.</span></span>  
  
 <span data-ttu-id="6e983-110">Když podmínky povolí, systém uvolňování paměti se může rozhodnout, že `gcTrimCommitOnLowMemory` Nastavení nepomůže aktuální aplikaci a ignorovat je.</span><span class="sxs-lookup"><span data-stu-id="6e983-110">When conditions permit, the garbage collector can decide that the `gcTrimCommitOnLowMemory` setting will not help the current application and ignore it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e983-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="6e983-111">Example</span></span>  
 <span data-ttu-id="6e983-112">Následující fragment kódu XML ukazuje, jak povolit `gcTrimCommitOnLowMemory` nastavení.</span><span class="sxs-lookup"><span data-stu-id="6e983-112">The following XML fragment shows how to enable the `gcTrimCommitOnLowMemory` setting.</span></span> <span data-ttu-id="6e983-113">Tři tečky označují další nastavení, která by byla v `runtime` uzlu.</span><span class="sxs-lookup"><span data-stu-id="6e983-113">Ellipses indicate other settings that would be in the `runtime` node.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6e983-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e983-114">See also</span></span>

- [<span data-ttu-id="6e983-115">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="6e983-115">Garbage Collection</span></span>](index.md)
