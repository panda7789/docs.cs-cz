---
title: Sestavení a souběžné spouštění
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fa44090e589e7a2a70b8fb7dbd8d5e6967c1ed19
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59126633"
---
# <a name="assemblies-and-side-by-side-execution"></a><span data-ttu-id="ea33c-102">Sestavení a souběžné spouštění</span><span class="sxs-lookup"><span data-stu-id="ea33c-102">Assemblies and Side-by-Side Execution</span></span>
<span data-ttu-id="ea33c-103">Vedle sebe spuštění je schopnost ukládat a spouštět více verzí aplikace nebo komponenty na stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="ea33c-103">Side-by-side execution is the ability to store and execute multiple versions of an application or component on the same computer.</span></span> <span data-ttu-id="ea33c-104">To znamená, že můžete mít více verzí modulu runtime a více verzí aplikací a komponent, které používají verzi modulu runtime, ve stejném počítači ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="ea33c-104">This means that you can have multiple versions of the runtime, and multiple versions of applications and components that use a version of the runtime, on the same computer at the same time.</span></span> <span data-ttu-id="ea33c-105">Vedle sebe spouštění dává větší kontrolu nad jakou verzí komponenty je aplikace propojena, a mít větší kontrolu nad jakou verzi modulu runtime aplikace používá.</span><span class="sxs-lookup"><span data-stu-id="ea33c-105">Side-by-side execution gives you more control over what versions of a component an application binds to, and more control over what version of the runtime an application uses.</span></span>  
  
 <span data-ttu-id="ea33c-106">Podpora úložiště vedle sebe a provádění různých verzí stejného sestavení je nedílnou součástí silné názvy a je součástí infrastruktury modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="ea33c-106">Support for side-by-side storage and execution of different versions of the same assembly is an integral part of strong naming and is built into the infrastructure of the runtime.</span></span> <span data-ttu-id="ea33c-107">Protože číslo verze sestavení silným názvem je součástí svoji identitu, modul runtime lze uložit více verzí stejného sestavení v globální mezipaměti sestavení a načtení těchto sestavení v době běhu.</span><span class="sxs-lookup"><span data-stu-id="ea33c-107">Because the strong-named assembly's version number is part of its identity, the runtime can store multiple versions of the same assembly in the global assembly cache and load those assemblies at run time.</span></span>  
  
 <span data-ttu-id="ea33c-108">I když se modul runtime poskytuje možnost vytvářet aplikace vedle sebe, není automatická spuštění vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="ea33c-108">Although the runtime provides you with the ability to create side-by-side applications, side-by-side execution is not automatic.</span></span> <span data-ttu-id="ea33c-109">Další informace o vytváření aplikací pro spuštění vedle sebe, naleznete v tématu [pokyny pro vytváření komponent pro spuštění vedle sebe](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span><span class="sxs-lookup"><span data-stu-id="ea33c-109">For more information on creating applications for side-by-side execution, see [Guidelines for Creating Components for Side-by-Side Execution](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea33c-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ea33c-110">See also</span></span>

- [<span data-ttu-id="ea33c-111">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="ea33c-111">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="ea33c-112">Sestavení v modulu CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="ea33c-112">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
