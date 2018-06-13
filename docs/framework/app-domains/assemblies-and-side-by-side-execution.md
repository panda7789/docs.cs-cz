---
title: Sestavení a souběžné spouštění
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 605cb6dfd3232d90d6c278f9563ac8d9f101b053
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752140"
---
# <a name="assemblies-and-side-by-side-execution"></a><span data-ttu-id="7e8e1-102">Sestavení a souběžné spouštění</span><span class="sxs-lookup"><span data-stu-id="7e8e1-102">Assemblies and Side-by-Side Execution</span></span>
<span data-ttu-id="7e8e1-103">Souběžného zpracování se možnost ukládat a spouštět více verzí aplikace nebo součásti na stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="7e8e1-103">Side-by-side execution is the ability to store and execute multiple versions of an application or component on the same computer.</span></span> <span data-ttu-id="7e8e1-104">To znamená, že můžete mít více verzí modulu runtime a více verzí aplikací a součástí, které používají verzi modulu runtime na stejném počítači ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="7e8e1-104">This means that you can have multiple versions of the runtime, and multiple versions of applications and components that use a version of the runtime, on the same computer at the same time.</span></span> <span data-ttu-id="7e8e1-105">Souběžně sdílená spouštění vám dává větší kontrolu nad jaké verze komponenty jsou svázány s aplikací a větší kontrolu nad jaká verze modulu runtime aplikace používá.</span><span class="sxs-lookup"><span data-stu-id="7e8e1-105">Side-by-side execution gives you more control over what versions of a component an application binds to, and more control over what version of the runtime an application uses.</span></span>  
  
 <span data-ttu-id="7e8e1-106">Podpora pro úložiště vedle sebe a provádění různých verzí stejného sestavení je nedílnou součástí silné názvy a je integrovaná do infrastrukturu modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="7e8e1-106">Support for side-by-side storage and execution of different versions of the same assembly is an integral part of strong naming and is built into the infrastructure of the runtime.</span></span> <span data-ttu-id="7e8e1-107">Číslo verze sestavení silným názvem je součástí svoji identitu, modul runtime můžete uložit více verzí stejného sestavení v globální mezipaměti sestavení a načtení těchto sestavení za běhu.</span><span class="sxs-lookup"><span data-stu-id="7e8e1-107">Because the strong-named assembly's version number is part of its identity, the runtime can store multiple versions of the same assembly in the global assembly cache and load those assemblies at run time.</span></span>  
  
 <span data-ttu-id="7e8e1-108">I když se modul runtime poskytuje schopnost vytvářet aplikace vedle sebe, není automatické spuštění vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="7e8e1-108">Although the runtime provides you with the ability to create side-by-side applications, side-by-side execution is not automatic.</span></span> <span data-ttu-id="7e8e1-109">Další informace o vytváření aplikací pro spuštění vedle sebe najdete v tématu [pokyny pro vytváření komponent pro spuštění vedle sebe](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span><span class="sxs-lookup"><span data-stu-id="7e8e1-109">For more information on creating applications for side-by-side execution, see [Guidelines for Creating Components for Side-by-Side Execution](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e8e1-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="7e8e1-110">See Also</span></span>  
 [<span data-ttu-id="7e8e1-111">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="7e8e1-111">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="7e8e1-112">Sestavení v modulu CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="7e8e1-112">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
