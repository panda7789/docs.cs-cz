---
title: "Výčty fúzí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged enumerations [.NET Framework], fusion
- fusion enumerations [.NET Framework]
- enumerations [.NET Framework fusion]
ms.assetid: 5817b4bc-b0ba-4b2f-a11c-a03dd8cb8f84
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f136f98758dc7162ec26323391e0c1295a8444f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="fusion-enumerations"></a><span data-ttu-id="6699b-102">Výčty fúzí</span><span class="sxs-lookup"><span data-stu-id="6699b-102">Fusion Enumerations</span></span>
<span data-ttu-id="6699b-103">Tato část popisuje nespravovaná vyčíslení, které používá fusion rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="6699b-103">This section describes the unmanaged enumerations that the fusion API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6699b-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="6699b-104">In This Section</span></span>  
 [<span data-ttu-id="6699b-105">ASM_CACHE_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="6699b-105">ASM_CACHE_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md)  
 <span data-ttu-id="6699b-106">Určuje zdroj sestavení reprezentována [iassemblycacheitem –](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="6699b-106">Indicates the source of an assembly represented by [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="6699b-107">ASM_CMP_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="6699b-107">ASM_CMP_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md)  
 <span data-ttu-id="6699b-108">Určuje verzi, sestavení, jazykovou verzi, podpisu a tak dále, dvě sestavení, který se má porovnat pomocí [iassemblyname::isequal –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-isequal-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="6699b-108">Indicates the version, build, culture, signature, and so on, of two assemblies to be compared by the [IAssemblyName::IsEqual](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-isequal-method.md) method.</span></span>  
  
 [<span data-ttu-id="6699b-109">ASM_DISPLAY_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="6699b-109">ASM_DISPLAY_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/asm-display-flags-enumeration.md)  
 <span data-ttu-id="6699b-110">Určuje verzi, sestavení, jazykovou verzi, podpisu a tak dále, sestavení, jehož zobrazovaný název bude načten pomocí [iassemblyname::GetDisplayName –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="6699b-110">Indicates the version, build, culture, signature, and so on, of the assembly whose display name will be retrieved by the [IAssemblyName::GetDisplayName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md) method.</span></span>  
  
 [<span data-ttu-id="6699b-111">ASM_NAME – výčet</span><span class="sxs-lookup"><span data-stu-id="6699b-111">ASM_NAME Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/asm-name-enumeration.md)  
 <span data-ttu-id="6699b-112">Určuje verzi, sestavení, jazykovou verzi, podpisu a tak dále, sestavení, jehož vlastnosti se načíst nebo nastavit [iassemblyname –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) metody.</span><span class="sxs-lookup"><span data-stu-id="6699b-112">Indicates the version, build, culture, signature, and so on, of the assembly whose properties will be retrieved or set by [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) methods.</span></span>  
  
 [<span data-ttu-id="6699b-113">AssemblyComparisonResult – výčet</span><span class="sxs-lookup"><span data-stu-id="6699b-113">AssemblyComparisonResult Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/assemblycomparisonresult-enumeration.md)  
 <span data-ttu-id="6699b-114">Označuje ekvivalenční dvě sestavení identit, počítáno od [compareassemblyidentity –](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="6699b-114">Indicates the equivalence of two assembly identities, as determined by the [CompareAssemblyIdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md) function.</span></span>  
  
 [<span data-ttu-id="6699b-115">CREATE_ASM_NAME_OBJ_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="6699b-115">CREATE_ASM_NAME_OBJ_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/create-asm-name-obj-flags-enumeration.md)  
 <span data-ttu-id="6699b-116">Určuje atributy `IAssemblyName` objektu, když je vytvořený pomocí [createassemblynameobject –](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="6699b-116">Specifies the attributes of an `IAssemblyName` object when it is constructed by the [CreateAssemblyNameObject](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md) function.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6699b-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="6699b-117">Related Sections</span></span>  
 [<span data-ttu-id="6699b-118">Rozhraní pro fúze</span><span class="sxs-lookup"><span data-stu-id="6699b-118">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
  
 [<span data-ttu-id="6699b-119">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="6699b-119">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
  
 [<span data-ttu-id="6699b-120">Struktury pro fúze</span><span class="sxs-lookup"><span data-stu-id="6699b-120">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
