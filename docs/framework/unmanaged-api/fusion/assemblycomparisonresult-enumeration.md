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
ms.openlocfilehash: 0086906b23cc65825bbd54a54e544fa9ec7b211e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796265"
---
# <a name="assemblycomparisonresult-enumeration"></a><span data-ttu-id="a392d-102">AssemblyComparisonResult – výčet</span><span class="sxs-lookup"><span data-stu-id="a392d-102">AssemblyComparisonResult Enumeration</span></span>
<span data-ttu-id="a392d-103">Označuje ekvivalent dvou identit sestavení, jak je určeno funkcí [CompareAssemblyIdentity –](compareassemblyidentity-function.md) .</span><span class="sxs-lookup"><span data-stu-id="a392d-103">Indicates the equivalence of two assembly identities, as determined by the [CompareAssemblyIdentity](compareassemblyidentity-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a392d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a392d-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="a392d-105">Členové</span><span class="sxs-lookup"><span data-stu-id="a392d-105">Members</span></span>  
  
|<span data-ttu-id="a392d-106">Název členu</span><span class="sxs-lookup"><span data-stu-id="a392d-106">Member name</span></span>|<span data-ttu-id="a392d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a392d-107">Description</span></span>|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|<span data-ttu-id="a392d-108">Označuje, že všechna pole sestavení v porovnání se shodují.</span><span class="sxs-lookup"><span data-stu-id="a392d-108">Indicates that all assembly fields in the comparison match.</span></span>|  
|`ACR_EquivalentFXUnified`|<span data-ttu-id="a392d-109">Označuje, že sestavení jsou považována za ekvivalentní na základě verze modulu CLR (Common Language Runtime) z sjednocení čísel verzí sestavení v .NET Framework verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="a392d-109">Indicates that assemblies are considered equivalent based on the common language runtime version (CLR) unification of assembly version numbers in the .NET Framework version 2.0.</span></span>|  
|`ACR_EquivalentPartialFXUnified`|<span data-ttu-id="a392d-110">Označuje částečnou shodu sestavení založenou na sjednocení CLR čísel verzí sestavení v .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="a392d-110">Indicates a partial match of the assemblies based on the CLR unification of assembly version numbers in the .NET Framework 2.0.</span></span>|  
|`ACR_EquivalentPartialMatch`|<span data-ttu-id="a392d-111">Označuje částečnou shodu sestavení.</span><span class="sxs-lookup"><span data-stu-id="a392d-111">Indicates a partial match of the assemblies.</span></span>|  
|`ACR_EquivalentPartialUnified`|<span data-ttu-id="a392d-112">Označuje částečnou shodu sestavení na základě zastaralého sjednocení čísel verzí.</span><span class="sxs-lookup"><span data-stu-id="a392d-112">Indicates a partial match of the assemblies based on legacy unification of version numbers.</span></span>|  
|`ACR_EquivalentPartialWeakNamed`|<span data-ttu-id="a392d-113">Označuje částečnou shodu jednoduše pojmenovaných sestavení.</span><span class="sxs-lookup"><span data-stu-id="a392d-113">Indicates a partial match of simply named assemblies.</span></span>|  
|`ACR_EquivalentUnified`|<span data-ttu-id="a392d-114">Označuje, že sestavení jsou považována za ekvivalentní na základě sjednocení čísel verzí ve starších verzích .NET Framework v rámci CLR.</span><span class="sxs-lookup"><span data-stu-id="a392d-114">Indicates that assemblies are considered equivalent based on the CLR unification of version numbers in legacy versions of the .NET Framework.</span></span>|  
|`ACR_EquivalentWeakNamed`|<span data-ttu-id="a392d-115">Označuje shodu mezi dvěma jednoduše pojmenovanými sestaveními, jejichž čísla verzí byla ignorována.</span><span class="sxs-lookup"><span data-stu-id="a392d-115">Indicates a match between two simply named assemblies whose version numbers were ignored.</span></span>|  
|`ACR_NonEquivalent`|<span data-ttu-id="a392d-116">Označuje, že mezi dvěma sestaveními nedošlo k žádné shodě.</span><span class="sxs-lookup"><span data-stu-id="a392d-116">Indicates that no match occurred between the two assemblies.</span></span>|  
|`ACR_NonEquivalentPartialVersion`|<span data-ttu-id="a392d-117">Označuje, že se dvě sestavení shodují s výjimkou jejich čísel verzí, která se shodují pouze částečně.</span><span class="sxs-lookup"><span data-stu-id="a392d-117">Indicates that the two assemblies match except for their version numbers, which match only partially.</span></span>|  
|`ACR_NonEquivalentVersion`|<span data-ttu-id="a392d-118">Označuje, že se dvě sestavení shodují s výjimkou jejich čísel verzí, která se neshodují.</span><span class="sxs-lookup"><span data-stu-id="a392d-118">Indicates that the two assemblies match except for their version numbers, which do not match.</span></span>|  
|`ACR_Unknown`|<span data-ttu-id="a392d-119">Označuje, že důvod nerovnocennosti není znám.</span><span class="sxs-lookup"><span data-stu-id="a392d-119">Indicates that the reason for non-equivalency is not known.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a392d-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a392d-120">Requirements</span></span>  
 <span data-ttu-id="a392d-121">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a392d-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a392d-122">**Hlaviček** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="a392d-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a392d-123">**Knihovna** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a392d-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a392d-124">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a392d-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a392d-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a392d-125">See also</span></span>

- [<span data-ttu-id="a392d-126">CompareAssemblyIdentity – funkce</span><span class="sxs-lookup"><span data-stu-id="a392d-126">CompareAssemblyIdentity Function</span></span>](compareassemblyidentity-function.md)
- [<span data-ttu-id="a392d-127">Výčty pro fúze</span><span class="sxs-lookup"><span data-stu-id="a392d-127">Fusion Enumerations</span></span>](fusion-enumerations.md)
