---
title: Používání obsluhovaných komponent s globální pamětí sestavení
description: Použití obsluhované komponenty (komponenty modelu COM+ spravovaného kódu) s globální mezipamětí sestavení v .NET. Podívejte se, zda CLR a služby COM+ mohou zpracovávat komponenty, které nejsou součástí GAC.
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache), serviced components
- serviced components, global assembly cache
- global assembly cache, serviced components
ms.assetid: 3423e5d9-234c-4571-8161-e35f6d130128
ms.openlocfilehash: 6b7371865b7b1cedda0ee03b2cc28c74b5c3da0b
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104478"
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a><span data-ttu-id="e438e-104">Používání obsluhovaných komponent s globální pamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="e438e-104">Using Serviced Components with the Global Assembly Cache</span></span>
<span data-ttu-id="e438e-105">Obsluhované komponenty (komponenty modelu COM+ spravovaného kódu) by měly být vloženy do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="e438e-105">Serviced components (managed code COM+ components) should be put in the Global Assembly Cache.</span></span> <span data-ttu-id="e438e-106">V některých scénářích může modul CLR (Common Language Runtime) a služby COM+ zpracovávat obsluhované komponenty, které nejsou v globální mezipaměti sestavení (GAC). v jiných scénářích to nemůže.</span><span class="sxs-lookup"><span data-stu-id="e438e-106">In some scenarios, the Common Language Runtime and COM+ Services can handle serviced components that are not in the Global Assembly Cache; in other scenarios, they cannot.</span></span> <span data-ttu-id="e438e-107">Tuto situaci ilustrují následující scénáře:</span><span class="sxs-lookup"><span data-stu-id="e438e-107">The following scenarios illustrate this:</span></span>  
  
- <span data-ttu-id="e438e-108">Pro obsluhované komponenty v serverové aplikaci COM+ musí být sestavení obsahující komponenty v globální mezipaměti sestavení (GAC), protože Dllhost.exe neběží ve stejném adresáři jako ten, který obsahuje komponenty služby.</span><span class="sxs-lookup"><span data-stu-id="e438e-108">For serviced components in a COM+ Server application, the assembly containing the components must be in the Global Assembly Cache, because Dllhost.exe does not run in the same directory as the one that contains the serviced components.</span></span>  
  
- <span data-ttu-id="e438e-109">Pro obsluhované komponenty v knihovně COM+ mohou moduly runtime a COM+ vyřešit odkaz na sestavení obsahující komponenty hledáním v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="e438e-109">For serviced components in a COM+ Library application, the runtime and COM+ Services can resolve the reference to the assembly containing the components by searching in the current directory.</span></span> <span data-ttu-id="e438e-110">V takovém případě nemusí být sestavení v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="e438e-110">In this case, the assembly does not have to be in the global assembly cache.</span></span>  
  
- <span data-ttu-id="e438e-111">Pro obsluhované komponenty v aplikaci ASP.NET se situace liší.</span><span class="sxs-lookup"><span data-stu-id="e438e-111">For serviced components in an ASP.NET application, the situation is different.</span></span> <span data-ttu-id="e438e-112">Pokud umístíte sestavení obsahující obsluhované komponenty do adresáře bin základní aplikace a použijete registraci na vyžádání, bude sestavení Stínově zkopírováno do mezipaměti pro stahování, protože ASP.NET využívá možnosti stínů modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="e438e-112">If you place the assembly containing the serviced components in the bin directory of the application base and use on-demand registration, the assembly will be shadow-copied into the download cache because ASP.NET leverages the shadow capabilities of the runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e438e-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="e438e-113">See also</span></span>

- [<span data-ttu-id="e438e-114">Práce se sestaveními a s globální pamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="e438e-114">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="e438e-115">Gacutil.exe (nástroj Global Assembly Cache Tool)</span><span class="sxs-lookup"><span data-stu-id="e438e-115">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
