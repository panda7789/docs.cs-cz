---
title: Sestavení a souběžné spouštění
ms.date: 08/20/2019
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6f5d4b6bf94300872f85c118bd149d12cea65d0
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973066"
---
# <a name="assemblies-and-side-by-side-execution"></a><span data-ttu-id="3004d-102">Sestavení a souběžné spouštění</span><span class="sxs-lookup"><span data-stu-id="3004d-102">Assemblies and side-by-side execution</span></span>
<span data-ttu-id="3004d-103">Souběžné spouštění je schopnost ukládat a spouštět více verzí aplikace nebo komponenty na stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="3004d-103">Side-by-side execution is the ability to store and execute multiple versions of an application or component on the same computer.</span></span> <span data-ttu-id="3004d-104">To znamená, že můžete mít více verzí modulu runtime a více verzí aplikací a komponent, které používají verzi modulu runtime, ve stejném počítači současně.</span><span class="sxs-lookup"><span data-stu-id="3004d-104">This means that you can have multiple versions of the runtime, and multiple versions of applications and components that use a version of the runtime, on the same computer at the same time.</span></span> <span data-ttu-id="3004d-105">Souběžné spouštění nabízí větší kontrolu nad tím, na které verze komponenty se aplikace váže, a lepší kontrolu nad tím, jakou verzi modulu runtime aplikace používá.</span><span class="sxs-lookup"><span data-stu-id="3004d-105">Side-by-side execution gives you more control over what versions of a component an application binds to, and more control over what version of the runtime an application uses.</span></span>  
  
 <span data-ttu-id="3004d-106">Podpora pro souběžné ukládání a provádění různých verzí stejného sestavení je nedílnou součástí silného pojmenování a je integrována do infrastruktury modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="3004d-106">Support for side-by-side storage and execution of different versions of the same assembly is an integral part of strong naming and is built into the infrastructure of the runtime.</span></span> <span data-ttu-id="3004d-107">Vzhledem k tomu, že číslo verze sestavení se silným názvem je součástí své identity, modul runtime může uložit více verzí stejného sestavení v globální mezipaměti sestavení (GAC) a načíst tato sestavení za běhu.</span><span class="sxs-lookup"><span data-stu-id="3004d-107">Because the strong-named assembly's version number is part of its identity, the runtime can store multiple versions of the same assembly in the global assembly cache and load those assemblies at run time.</span></span>  
  
 <span data-ttu-id="3004d-108">I když modul runtime poskytuje možnost vytvářet souběžné aplikace, nejedná se o automatické spuštění souběžného spouštění.</span><span class="sxs-lookup"><span data-stu-id="3004d-108">Although the runtime provides you with the ability to create side-by-side applications, side-by-side execution is not automatic.</span></span> <span data-ttu-id="3004d-109">Další informace o vytváření aplikací pro souběžné spouštění najdete v tématu [pokyny pro vytváření komponent pro souběžné spouštění](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span><span class="sxs-lookup"><span data-stu-id="3004d-109">For more information on creating applications for side-by-side execution, see [Guidelines for creating components for side-by-side execution](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3004d-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3004d-110">See also</span></span>

- [<span data-ttu-id="3004d-111">Způsob, jakým modul runtime vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="3004d-111">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="3004d-112">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="3004d-112">Assemblies in .NET</span></span>](index.md)
