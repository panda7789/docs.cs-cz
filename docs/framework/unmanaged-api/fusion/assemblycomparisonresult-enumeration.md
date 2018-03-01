---
title: "AssemblyComparisonResult – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- AssemblyComparisonResult
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- AssemblyComparisonResult
helpviewer_keywords:
- AssemblyComparisonResult enumeration [.NET Framework fusion]
ms.assetid: bd042f89-10b1-40ca-946e-46da082f5263
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f2c38561a804a331df102a600d4b0b0f6312aaa6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="assemblycomparisonresult-enumeration"></a><span data-ttu-id="25b99-102">AssemblyComparisonResult – výčet</span><span class="sxs-lookup"><span data-stu-id="25b99-102">AssemblyComparisonResult Enumeration</span></span>
<span data-ttu-id="25b99-103">Označuje ekvivalenční dvě sestavení identit, počítáno od [compareassemblyidentity –](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="25b99-103">Indicates the equivalence of two assembly identities, as determined by the [CompareAssemblyIdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25b99-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25b99-104">Syntax</span></span>  
  
```  
typedef enum _tagAssemblyComparisonResult {  
    ACR_Unknown,   
    ACR_EquivalentFullMatch,  
    ACR_EquivalentWeakNamed,  
    ACR_EquivalentFXUnified,  
    ACR_EquivalentUnified,    
    ACR_NonEquivalentVersion,  
    ACR_NonEquivalent,      
    ACR_EquivalentPartialMatch,  
    ACR_EquivalentPartialWeakNamed,    
    ACR_EquivalentPartialUnified,  
    ACR_EquivalentPartialFXUnified,  
    ACR_NonEquivalentPartialVersion    
} AssemblyComparisonResult;  
```  
  
## <a name="members"></a><span data-ttu-id="25b99-105">Členové</span><span class="sxs-lookup"><span data-stu-id="25b99-105">Members</span></span>  
  
|<span data-ttu-id="25b99-106">Název členu</span><span class="sxs-lookup"><span data-stu-id="25b99-106">Member name</span></span>|<span data-ttu-id="25b99-107">Popis</span><span class="sxs-lookup"><span data-stu-id="25b99-107">Description</span></span>|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|<span data-ttu-id="25b99-108">Označuje, že všechny sestavení polí v porovnání shody.</span><span class="sxs-lookup"><span data-stu-id="25b99-108">Indicates that all assembly fields in the comparison match.</span></span>|  
|`ACR_EquivalentFXUnified`|<span data-ttu-id="25b99-109">Označuje, že sestavení jsou považovány za ekvivalentní založené na běžné sjednocením runtime verze (CLR) jazyk čísla verzí sestavení v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="25b99-109">Indicates that assemblies are considered equivalent based on the common language runtime version (CLR) unification of assembly version numbers in the .NET Framework version 2.0.</span></span>|  
|`ACR_EquivalentPartialFXUnified`|<span data-ttu-id="25b99-110">Označuje částečnou shodu sestavení podle CLR sjednocením čísla verzí sestavení v rozhraní .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="25b99-110">Indicates a partial match of the assemblies based on the CLR unification of assembly version numbers in the .NET Framework 2.0.</span></span>|  
|`ACR_EquivalentPartialMatch`|<span data-ttu-id="25b99-111">Označuje částečnou shodu sestavení.</span><span class="sxs-lookup"><span data-stu-id="25b99-111">Indicates a partial match of the assemblies.</span></span>|  
|`ACR_EquivalentPartialUnified`|<span data-ttu-id="25b99-112">Označuje částečnou shodu sestavení založené na starší verze sjednocení čísla verzí.</span><span class="sxs-lookup"><span data-stu-id="25b99-112">Indicates a partial match of the assemblies based on legacy unification of version numbers.</span></span>|  
|`ACR_EquivalentPartialWeakNamed`|<span data-ttu-id="25b99-113">Označuje částečnou shodu jednoduše pojmenované sestavení.</span><span class="sxs-lookup"><span data-stu-id="25b99-113">Indicates a partial match of simply named assemblies.</span></span>|  
|`ACR_EquivalentUnified`|<span data-ttu-id="25b99-114">Označuje, že sestavení jsou považovány za ekvivalentní podle sjednocení CLR verze čísel ve starších verzích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="25b99-114">Indicates that assemblies are considered equivalent based on the CLR unification of version numbers in legacy versions of the .NET Framework.</span></span>|  
|`ACR_EquivalentWeakNamed`|<span data-ttu-id="25b99-115">Označuje shodu mezi dvěma jednoduše pojmenované sestavení jejichž čísla verzí byly ignorovány.</span><span class="sxs-lookup"><span data-stu-id="25b99-115">Indicates a match between two simply named assemblies whose version numbers were ignored.</span></span>|  
|`ACR_NonEquivalent`|<span data-ttu-id="25b99-116">Označuje, že žádná shoda došlo mezi dvěma sestavení.</span><span class="sxs-lookup"><span data-stu-id="25b99-116">Indicates that no match occurred between the two assemblies.</span></span>|  
|`ACR_NonEquivalentPartialVersion`|<span data-ttu-id="25b99-117">Označuje, že dvě sestavení shodovat s výjimkou jejich čísla verzí, které se shodují jen částečně.</span><span class="sxs-lookup"><span data-stu-id="25b99-117">Indicates that the two assemblies match except for their version numbers, which match only partially.</span></span>|  
|`ACR_NonEquivalentVersion`|<span data-ttu-id="25b99-118">Označuje, že dvě sestavení shodovat s výjimkou jejich čísla verzí, které se neshodují.</span><span class="sxs-lookup"><span data-stu-id="25b99-118">Indicates that the two assemblies match except for their version numbers, which do not match.</span></span>|  
|`ACR_Unknown`|<span data-ttu-id="25b99-119">Označuje, že důvod zajištění rovnocennosti není znám.</span><span class="sxs-lookup"><span data-stu-id="25b99-119">Indicates that the reason for non-equivalency is not known.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="25b99-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="25b99-120">Requirements</span></span>  
 <span data-ttu-id="25b99-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25b99-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25b99-122">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="25b99-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="25b99-123">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="25b99-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="25b99-124">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25b99-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25b99-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="25b99-125">See Also</span></span>  
 [<span data-ttu-id="25b99-126">CompareAssemblyIdentity – funkce</span><span class="sxs-lookup"><span data-stu-id="25b99-126">CompareAssemblyIdentity Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)  
 [<span data-ttu-id="25b99-127">Výčty pro fúze</span><span class="sxs-lookup"><span data-stu-id="25b99-127">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
