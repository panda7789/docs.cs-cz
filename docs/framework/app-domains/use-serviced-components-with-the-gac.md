---
title: Používání obsluhovaných komponent s globální pamětí sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache), serviced components
- serviced components, global assembly cache
- global assembly cache, serviced components
ms.assetid: 3423e5d9-234c-4571-8161-e35f6d130128
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60d42fa296585d26186a2e75a49c5b3cf761e846
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583243"
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a><span data-ttu-id="65fe7-102">Používání obsluhovaných komponent s globální pamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="65fe7-102">Using Serviced Components with the Global Assembly Cache</span></span>
<span data-ttu-id="65fe7-103">Obsluhované komponenty (spravované komponenty modelu COM +) měly být umístěny v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="65fe7-103">Serviced components (managed code COM+ components) should be put in the Global Assembly Cache.</span></span> <span data-ttu-id="65fe7-104">V některých scénářích modul Common Language Runtime a služby COM + zvládne obsluhované komponenty, které nejsou v globální mezipaměti sestavení; v jiných situacích možné.</span><span class="sxs-lookup"><span data-stu-id="65fe7-104">In some scenarios, the Common Language Runtime and COM+ Services can handle serviced components that are not in the Global Assembly Cache; in other scenarios, they cannot.</span></span> <span data-ttu-id="65fe7-105">Následující scénáře popisují toto:</span><span class="sxs-lookup"><span data-stu-id="65fe7-105">The following scenarios illustrate this:</span></span>  
  
-   <span data-ttu-id="65fe7-106">Obsluhované komponenty v aplikaci COM + Server sestavení obsahující komponenty musí být v globální mezipaměti sestavení, protože Dllhost.exe nejde spustit ve stejném adresáři jako ten, který obsahuje obsluhované komponenty.</span><span class="sxs-lookup"><span data-stu-id="65fe7-106">For serviced components in a COM+ Server application, the assembly containing the components must be in the Global Assembly Cache, because Dllhost.exe does not run in the same directory as the one that contains the serviced components.</span></span>  
  
-   <span data-ttu-id="65fe7-107">Pro obsluhované komponenty v aplikaci knihovny modelu COM + modul runtime a služby COM + přeložit odkaz na sestavení obsahující komponenty tak, že v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="65fe7-107">For serviced components in a COM+ Library application, the runtime and COM+ Services can resolve the reference to the assembly containing the components by searching in the current directory.</span></span> <span data-ttu-id="65fe7-108">Sestavení v takovém případě nemusí být v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="65fe7-108">In this case, the assembly does not have to be in the global assembly cache.</span></span>  
  
-   <span data-ttu-id="65fe7-109">Pro obsluhované komponenty v aplikaci ASP.NET se situace liší.</span><span class="sxs-lookup"><span data-stu-id="65fe7-109">For serviced components in an ASP.NET application, the situation is different.</span></span> <span data-ttu-id="65fe7-110">Pokud umístíte sestavení obsahující obsluhované komponenty v adresáři bin základ cesty aplikace a používat na vyžádání registraci, bude sestavení stínové zkopírována do mezipaměti pro stahování vzhledem k tomu, že technologie ASP.NET využívá stínové možnosti modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="65fe7-110">If you place the assembly containing the serviced components in the bin directory of the application base and use on-demand registration, the assembly will be shadow-copied into the download cache because ASP.NET leverages the shadow capabilities of the runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65fe7-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65fe7-111">See also</span></span>
- [<span data-ttu-id="65fe7-112">Práce se sestaveními a s globální pamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="65fe7-112">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="65fe7-113">Gacutil.exe (nástroj globální mezipaměti sestavení)</span><span class="sxs-lookup"><span data-stu-id="65fe7-113">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
