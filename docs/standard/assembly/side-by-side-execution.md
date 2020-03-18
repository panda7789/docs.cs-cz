---
title: Sestavení a souběžné spouštění
ms.date: 08/20/2019
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
ms.openlocfilehash: 234efba66d87b520b54d6d113afcc4bba0bfe06a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138665"
---
# <a name="assemblies-and-side-by-side-execution"></a><span data-ttu-id="6fef1-102">Sestavení a souběžné spouštění</span><span class="sxs-lookup"><span data-stu-id="6fef1-102">Assemblies and side-by-side execution</span></span>

<span data-ttu-id="6fef1-103">Souběžné spuštění je možnost ukládat a spouštět více verzí aplikace nebo součásti ve stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="6fef1-103">Side-by-side execution is the ability to store and execute multiple versions of an application or component on the same computer.</span></span> <span data-ttu-id="6fef1-104">To znamená, že můžete mít více verzí runtime a více verzí aplikací a součástí, které používají verzi runtime, ve stejném počítači ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="6fef1-104">This means that you can have multiple versions of the runtime, and multiple versions of applications and components that use a version of the runtime, on the same computer at the same time.</span></span> <span data-ttu-id="6fef1-105">Souběžné spuštění poskytuje větší kontrolu nad tím, jaké verze součásti aplikace váže, a větší kontrolu nad tím, jakou verzi runtime aplikace používá.</span><span class="sxs-lookup"><span data-stu-id="6fef1-105">Side-by-side execution gives you more control over what versions of a component an application binds to, and more control over what version of the runtime an application uses.</span></span>  
  
<span data-ttu-id="6fef1-106">Podpora pro souběžné úložiště a provádění různých verzí stejného sestavení je nedílnou součástí silného pojmenování a je integrována do infrastruktury runtime.</span><span class="sxs-lookup"><span data-stu-id="6fef1-106">Support for side-by-side storage and execution of different versions of the same assembly is an integral part of strong naming and is built into the infrastructure of the runtime.</span></span> <span data-ttu-id="6fef1-107">Vzhledem k tomu, že číslo verze sestavení se silným názvem je součástí jeho identity, může za běhu uložit více verzí stejného sestavení do globální mezipaměti sestavení a načíst tato sestavení za běhu.</span><span class="sxs-lookup"><span data-stu-id="6fef1-107">Because the strong-named assembly's version number is part of its identity, the runtime can store multiple versions of the same assembly in the global assembly cache and load those assemblies at run time.</span></span>  
  
<span data-ttu-id="6fef1-108">Přestože runtime poskytuje možnost vytvářet souběžné aplikace, souběžné spuštění není automatické.</span><span class="sxs-lookup"><span data-stu-id="6fef1-108">Although the runtime provides you with the ability to create side-by-side applications, side-by-side execution is not automatic.</span></span> <span data-ttu-id="6fef1-109">Další informace o vytváření aplikací pro souběžné spuštění naleznete v [tématu Pokyny pro vytváření komponent pro souběžné spuštění](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span><span class="sxs-lookup"><span data-stu-id="6fef1-109">For more information on creating applications for side-by-side execution, see [Guidelines for creating components for side-by-side execution](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fef1-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="6fef1-110">See also</span></span>

- [<span data-ttu-id="6fef1-111">Jak runtime vyhledá sestavení</span><span class="sxs-lookup"><span data-stu-id="6fef1-111">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="6fef1-112">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="6fef1-112">Assemblies in .NET</span></span>](index.md)
