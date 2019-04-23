---
title: AssemblyComparisonResult – výčet
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03b8ecc996e14263510e2d0a658cec020696c263
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59141697"
---
# <a name="assemblycomparisonresult-enumeration"></a><span data-ttu-id="16c9c-102">AssemblyComparisonResult – výčet</span><span class="sxs-lookup"><span data-stu-id="16c9c-102">AssemblyComparisonResult Enumeration</span></span>
<span data-ttu-id="16c9c-103">Označuje ekvivalence dvě sestavení identity, počítáno od [compareassemblyidentity –](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="16c9c-103">Indicates the equivalence of two assembly identities, as determined by the [CompareAssemblyIdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16c9c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16c9c-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="16c9c-105">Členové</span><span class="sxs-lookup"><span data-stu-id="16c9c-105">Members</span></span>  
  
|<span data-ttu-id="16c9c-106">Název členu</span><span class="sxs-lookup"><span data-stu-id="16c9c-106">Member name</span></span>|<span data-ttu-id="16c9c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="16c9c-107">Description</span></span>|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|<span data-ttu-id="16c9c-108">Označuje, že všechna sestavení pole v porovnání shody.</span><span class="sxs-lookup"><span data-stu-id="16c9c-108">Indicates that all assembly fields in the comparison match.</span></span>|  
|`ACR_EquivalentFXUnified`|<span data-ttu-id="16c9c-109">Označuje, že sestavení jsou považovány za ekvivalentní založené na běžných sjednocení modul runtime verze (CLR) jazyka čísla verze sestavení v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="16c9c-109">Indicates that assemblies are considered equivalent based on the common language runtime version (CLR) unification of assembly version numbers in the .NET Framework version 2.0.</span></span>|  
|`ACR_EquivalentPartialFXUnified`|<span data-ttu-id="16c9c-110">Označuje částečnou shodu sestavení založená na modulu CLR sjednocení čísla verze sestavení v rozhraní .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="16c9c-110">Indicates a partial match of the assemblies based on the CLR unification of assembly version numbers in the .NET Framework 2.0.</span></span>|  
|`ACR_EquivalentPartialMatch`|<span data-ttu-id="16c9c-111">Označuje částečnou shodu sestavení.</span><span class="sxs-lookup"><span data-stu-id="16c9c-111">Indicates a partial match of the assemblies.</span></span>|  
|`ACR_EquivalentPartialUnified`|<span data-ttu-id="16c9c-112">Označuje částečnou shodu sestavení založená na starší verzi sjednocení čísla verzí.</span><span class="sxs-lookup"><span data-stu-id="16c9c-112">Indicates a partial match of the assemblies based on legacy unification of version numbers.</span></span>|  
|`ACR_EquivalentPartialWeakNamed`|<span data-ttu-id="16c9c-113">Označuje částečnou shodu s jednoduchým názvem sestavení.</span><span class="sxs-lookup"><span data-stu-id="16c9c-113">Indicates a partial match of simply named assemblies.</span></span>|  
|`ACR_EquivalentUnified`|<span data-ttu-id="16c9c-114">Označuje, že sestavení jsou považovány za ekvivalentní podle sjednocení CLR verze čísel ve starších verzích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16c9c-114">Indicates that assemblies are considered equivalent based on the CLR unification of version numbers in legacy versions of the .NET Framework.</span></span>|  
|`ACR_EquivalentWeakNamed`|<span data-ttu-id="16c9c-115">Označuje shodu mezi dvěma s jednoduchým názvem sestavení, jejichž čísla verze byly ignorovány.</span><span class="sxs-lookup"><span data-stu-id="16c9c-115">Indicates a match between two simply named assemblies whose version numbers were ignored.</span></span>|  
|`ACR_NonEquivalent`|<span data-ttu-id="16c9c-116">Označuje, že žádná shoda, která proběhla mezi dvě sestavení.</span><span class="sxs-lookup"><span data-stu-id="16c9c-116">Indicates that no match occurred between the two assemblies.</span></span>|  
|`ACR_NonEquivalentPartialVersion`|<span data-ttu-id="16c9c-117">Označuje, že daná dvě sestavení shodovat s výjimkou čísla verze, které se shodují jen částečně.</span><span class="sxs-lookup"><span data-stu-id="16c9c-117">Indicates that the two assemblies match except for their version numbers, which match only partially.</span></span>|  
|`ACR_NonEquivalentVersion`|<span data-ttu-id="16c9c-118">Označuje, že tato dvě sestavení shodovat s výjimkou jejich čísla verzí, které se neshodují.</span><span class="sxs-lookup"><span data-stu-id="16c9c-118">Indicates that the two assemblies match except for their version numbers, which do not match.</span></span>|  
|`ACR_Unknown`|<span data-ttu-id="16c9c-119">Označuje, že-do referenčních materiálech o ekvivalenci důvod není znám.</span><span class="sxs-lookup"><span data-stu-id="16c9c-119">Indicates that the reason for non-equivalency is not known.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="16c9c-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="16c9c-120">Requirements</span></span>  
 <span data-ttu-id="16c9c-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16c9c-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16c9c-122">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="16c9c-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="16c9c-123">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="16c9c-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="16c9c-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16c9c-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16c9c-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="16c9c-125">See also</span></span>

- [<span data-ttu-id="16c9c-126">CompareAssemblyIdentity – funkce</span><span class="sxs-lookup"><span data-stu-id="16c9c-126">CompareAssemblyIdentity Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)
- [<span data-ttu-id="16c9c-127">Výčty pro fúze</span><span class="sxs-lookup"><span data-stu-id="16c9c-127">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
