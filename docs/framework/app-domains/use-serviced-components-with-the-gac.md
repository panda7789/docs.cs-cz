---
title: "Používání obsluhovaných komponent s globální pamětí sestavení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache), serviced components
- serviced components, global assembly cache
- global assembly cache, serviced components
ms.assetid: 3423e5d9-234c-4571-8161-e35f6d130128
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 45fd02c4f87d33766741e6fd023f9b40b9964d63
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a><span data-ttu-id="a3da9-102">Používání obsluhovaných komponent s globální pamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="a3da9-102">Using Serviced Components with the Global Assembly Cache</span></span>
<span data-ttu-id="a3da9-103">Obsluhované komponenty (spravované komponenty modelu COM +) měly být umístěny v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="a3da9-103">Serviced components (managed code COM+ components) should be put in the global assembly cache.</span></span> <span data-ttu-id="a3da9-104">V některých scénářích modul common language runtime a služby COM + může zpracovávat obsluhované komponenty, které nejsou v globální mezipaměti sestavení; v jiných scénářích nelze.</span><span class="sxs-lookup"><span data-stu-id="a3da9-104">In some scenarios, the common language runtime and COM+ Services can handle serviced components that are not in the global assembly cache; in other scenarios, they cannot.</span></span> <span data-ttu-id="a3da9-105">Následující scénáře popisují toto:</span><span class="sxs-lookup"><span data-stu-id="a3da9-105">The following scenarios illustrate this:</span></span>  
  
-   <span data-ttu-id="a3da9-106">Obsluhované komponenty aplikace modelu COM + serveru sestavení obsahující komponenty musí být v globální mezipaměti sestavení, protože Dllhost.exe nejde spustit ve stejném adresáři jako ta, která obsahuje obsluhované komponenty.</span><span class="sxs-lookup"><span data-stu-id="a3da9-106">For serviced components in a COM+ Server application, the assembly containing the components must be in the global assembly cache, because Dllhost.exe does not run in the same directory as the one that contains the serviced components.</span></span>  
  
-   <span data-ttu-id="a3da9-107">Pro obsluhované komponenty aplikace modelu COM + knihovny modulu runtime a služby COM + přeložit odkaz na sestavení obsahující komponenty pomocí vyhledávání v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="a3da9-107">For serviced components in a COM+ Library application, the runtime and COM+ Services can resolve the reference to the assembly containing the components by searching in the current directory.</span></span> <span data-ttu-id="a3da9-108">Sestavení v takovém případě nemusí být v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="a3da9-108">In this case, the assembly does not have to be in the global assembly cache.</span></span>  
  
-   <span data-ttu-id="a3da9-109">Obsluhované komponenty v aplikaci ASP.NET je různé situace.</span><span class="sxs-lookup"><span data-stu-id="a3da9-109">For serviced components in an ASP.NET application, the situation is different.</span></span> <span data-ttu-id="a3da9-110">Pokud umístíte sestavení obsahující obsluhované komponenty v adresáři bin základu aplikace a použijete registrace na vyžádání, sestavení bude vytvořena stínová kopie mezipaměť pro stahování protože ASP.NET využívá možnosti stínové kopie modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="a3da9-110">If you place the assembly containing the serviced components in the bin directory of the application base and use on-demand registration, the assembly will be shadow-copied into the download cache because ASP.NET leverages the shadow capabilities of the runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3da9-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="a3da9-111">See Also</span></span>  
 [<span data-ttu-id="a3da9-112">Práce se sestaveními a globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="a3da9-112">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="a3da9-113">Gacutil.exe (nástroj globální mezipaměti sestavení)</span><span class="sxs-lookup"><span data-stu-id="a3da9-113">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
