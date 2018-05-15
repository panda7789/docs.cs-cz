---
title: 'Postupy: Odebrání sestavení z globální mezipaměti sestavení'
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- global assembly cache, removing assemblies
- strong-named assemblies, global assembly cache
- removing assemblies from global assembly cache
- deleting assemblies in global assembly cache
- Global Assembly Cache tool
- GAC (global assembly cache), removing assemblies
ms.assetid: acdcc588-b458-436d-876c-726de68244c1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c5f47f4c33f725377281146bef0a37dbd3f774c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-remove-an-assembly-from-the-global-assembly-cache"></a><span data-ttu-id="662aa-102">Postupy: Odebrání sestavení z globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="662aa-102">How to: Remove an Assembly from the Global Assembly Cache</span></span>
<span data-ttu-id="662aa-103">Existují dva způsoby, jak odebrání sestavení z globální mezipaměti sestavení (GAC):</span><span class="sxs-lookup"><span data-stu-id="662aa-103">There are two ways to remove an assembly from the global assembly cache (GAC):</span></span>  
  
-   <span data-ttu-id="662aa-104">Pomocí [nástroj globální mezipaměti sestavení (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="662aa-104">By using the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span></span> <span data-ttu-id="662aa-105">Tato možnost slouží k odinstalaci sestavení, které jste umístili do mezipaměti GAC během vývoje a testování.</span><span class="sxs-lookup"><span data-stu-id="662aa-105">You can use this option to uninstall assemblies that you've placed in the GAC during development and testing.</span></span>  
  
-   <span data-ttu-id="662aa-106">Pomocí [Instalační služby systému Windows](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx).</span><span class="sxs-lookup"><span data-stu-id="662aa-106">By using [Windows Installer](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx).</span></span> <span data-ttu-id="662aa-107">Tuto možnost používejte Odinstalace sestavení při testování instalační balíčky a pro produkční systémy.</span><span class="sxs-lookup"><span data-stu-id="662aa-107">You should use this option to uninstall assemblies when testing installation packages and for production systems.</span></span>  
  
### <a name="removing-an-assembly-with-gacutilexe"></a><span data-ttu-id="662aa-108">Odebrání sestavení s Gacutil.exe</span><span class="sxs-lookup"><span data-stu-id="662aa-108">Removing an assembly with Gacutil.exe</span></span>  
  
1.  <span data-ttu-id="662aa-109">V příkazovém řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="662aa-109">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="662aa-110">**Gacutil – u** \< *název sestavení*></span><span class="sxs-lookup"><span data-stu-id="662aa-110">**gacutil –u** \<*assembly name*></span></span>  
  
     <span data-ttu-id="662aa-111">V tomto příkazu *název sestavení* je název sestavení pro odebrání z globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="662aa-111">In this command, *assembly name* is the name of the assembly to remove from the global assembly cache.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="662aa-112">Neměli byste používat Gacutil.exe odebrat z důvodu možnost, že sestavení může stále nutné některé aplikace sestavení na produkční systémy.</span><span class="sxs-lookup"><span data-stu-id="662aa-112">You should not use Gacutil.exe to remove assemblies on production systems because of the possibility that the assembly may still be required by some application.</span></span> <span data-ttu-id="662aa-113">Místo toho používejte Instalační služby systému Windows, který udržuje počet odkazů pro každé sestavení, kdy se instaluje v mezipaměti GAC.</span><span class="sxs-lookup"><span data-stu-id="662aa-113">Instead, you should use the Windows Installer, which maintains a reference count for each assembly it installs in the GAC.</span></span>  
  
 <span data-ttu-id="662aa-114">Následující příklad odebere sestavení s názvem `hello.dll` z globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="662aa-114">The following example removes an assembly named `hello.dll` from the global assembly cache.</span></span>  
  
```  
gacutil -u hello  
```  
  
### <a name="removing-an-assembly-with-windows-installer"></a><span data-ttu-id="662aa-115">Odebrání sestavení s Instalační služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="662aa-115">Removing an assembly with Windows Installer</span></span>  
  
1.  <span data-ttu-id="662aa-116">Z **programy a funkce** aplikace v **ovládací panely**, vyberte aplikaci, kterou chcete odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="662aa-116">From the **Programs and Features** app in **Control Panel**, select the app that you want to uninstall.</span></span> <span data-ttu-id="662aa-117">Pokud se instalační balíček umístit sestavení v mezipaměti GAC, instalační služba systému Windows, budou odebrány Pokud nejsou použity v jiné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="662aa-117">If the installation package placed assemblies in the GAC, Windows Installer will remove them if they are not used by another application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="662aa-118">Instalační služba systému Windows udržuje počet odkazů pro sestavení, které jsou nainstalované v mezipaměti GAC.</span><span class="sxs-lookup"><span data-stu-id="662aa-118">Windows Installer maintains a reference count for assemblies installed in the GAC.</span></span> <span data-ttu-id="662aa-119">Sestavení se odebere z mezipaměti GAC jenom v případě, že jeho počet odkazů hodnota nula, který označuje, že není používán žádnou aplikaci nainstalovat balíček Instalační služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="662aa-119">An assembly is removed from the GAC only when its reference count reaches zero, which indicates that it is not used by any application installed by a Windows Installer package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="662aa-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="662aa-120">See Also</span></span>  
 [<span data-ttu-id="662aa-121">Práce se sestaveními a s globální pamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="662aa-121">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="662aa-122">Postupy: Instalace sestavení do globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="662aa-122">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 [<span data-ttu-id="662aa-123">Gacutil.exe (nástroj globální mezipaměti sestavení)</span><span class="sxs-lookup"><span data-stu-id="662aa-123">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
