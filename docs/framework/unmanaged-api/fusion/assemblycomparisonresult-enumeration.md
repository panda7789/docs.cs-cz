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
ms.openlocfilehash: e3cdb648397ca4f4aa2326e4f2349a5a14c3edcc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178295"
---
# <a name="assemblycomparisonresult-enumeration"></a><span data-ttu-id="dfd6f-102">AssemblyComparisonResult – výčet</span><span class="sxs-lookup"><span data-stu-id="dfd6f-102">AssemblyComparisonResult Enumeration</span></span>
<span data-ttu-id="dfd6f-103">Označuje rovnocennost dvou identit sestavení, jak je určeno [CompareAssemblyIdentity](compareassemblyidentity-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="dfd6f-103">Indicates the equivalence of two assembly identities, as determined by the [CompareAssemblyIdentity](compareassemblyidentity-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfd6f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dfd6f-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="dfd6f-105">Členové</span><span class="sxs-lookup"><span data-stu-id="dfd6f-105">Members</span></span>  
  
|<span data-ttu-id="dfd6f-106">Název členu</span><span class="sxs-lookup"><span data-stu-id="dfd6f-106">Member name</span></span>|<span data-ttu-id="dfd6f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="dfd6f-107">Description</span></span>|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|<span data-ttu-id="dfd6f-108">Označuje, že všechna pole sestavení v porovnání odpovídají.</span><span class="sxs-lookup"><span data-stu-id="dfd6f-108">Indicates that all assembly fields in the comparison match.</span></span>|  
|`ACR_EquivalentFXUnified`|<span data-ttu-id="dfd6f-109">Označuje, že sestavení jsou považovány za ekvivalentní na základě sjednocení čísla verzí sestavení v rozhraní .NET Framework verze 2.0 ve verzi CLR (CLR) ve společném jazyce.</span><span class="sxs-lookup"><span data-stu-id="dfd6f-109">Indicates that assemblies are considered equivalent based on the common language runtime version (CLR) unification of assembly version numbers in the .NET Framework version 2.0.</span></span>|  
|`ACR_EquivalentPartialFXUnified`|<span data-ttu-id="dfd6f-110">Označuje částečnou shodu sestavení na základě sjednocení CLR čísel verzí sestavení v rozhraní .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="dfd6f-110">Indicates a partial match of the assemblies based on the CLR unification of assembly version numbers in the .NET Framework 2.0.</span></span>|  
|`ACR_EquivalentPartialMatch`|<span data-ttu-id="dfd6f-111">Označuje částečnou shodu sestavení.</span><span class="sxs-lookup"><span data-stu-id="dfd6f-111">Indicates a partial match of the assemblies.</span></span>|  
|`ACR_EquivalentPartialUnified`|<span data-ttu-id="dfd6f-112">Označuje částečnou shodu sestavení na základě staršího sjednocení čísel verzí.</span><span class="sxs-lookup"><span data-stu-id="dfd6f-112">Indicates a partial match of the assemblies based on legacy unification of version numbers.</span></span>|  
|`ACR_EquivalentPartialWeakNamed`|<span data-ttu-id="dfd6f-113">Označuje částečnou shodu jednoduše pojmenovaných sestavení.</span><span class="sxs-lookup"><span data-stu-id="dfd6f-113">Indicates a partial match of simply named assemblies.</span></span>|  
|`ACR_EquivalentUnified`|<span data-ttu-id="dfd6f-114">Označuje, že sestavení jsou považovány za ekvivalentní na základě clr sjednocení čísel verzí ve starších verzích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dfd6f-114">Indicates that assemblies are considered equivalent based on the CLR unification of version numbers in legacy versions of the .NET Framework.</span></span>|  
|`ACR_EquivalentWeakNamed`|<span data-ttu-id="dfd6f-115">Označuje shodu mezi dvěma jednoduše pojmenovanými sestaveními, jejichž čísla verzí byla ignorována.</span><span class="sxs-lookup"><span data-stu-id="dfd6f-115">Indicates a match between two simply named assemblies whose version numbers were ignored.</span></span>|  
|`ACR_NonEquivalent`|<span data-ttu-id="dfd6f-116">Označuje, že mezi dvěma sestaveními nedošlo k žádné shodě.</span><span class="sxs-lookup"><span data-stu-id="dfd6f-116">Indicates that no match occurred between the two assemblies.</span></span>|  
|`ACR_NonEquivalentPartialVersion`|<span data-ttu-id="dfd6f-117">Označuje, že dvě sestavení odpovídají s výjimkou jejich čísel verzí, které odpovídají pouze částečně.</span><span class="sxs-lookup"><span data-stu-id="dfd6f-117">Indicates that the two assemblies match except for their version numbers, which match only partially.</span></span>|  
|`ACR_NonEquivalentVersion`|<span data-ttu-id="dfd6f-118">Označuje, že dvě sestavení odpovídají s výjimkou jejich čísla verzí, které se neshodují.</span><span class="sxs-lookup"><span data-stu-id="dfd6f-118">Indicates that the two assemblies match except for their version numbers, which do not match.</span></span>|  
|`ACR_Unknown`|<span data-ttu-id="dfd6f-119">Označuje, že důvod neekvivalence není znám.</span><span class="sxs-lookup"><span data-stu-id="dfd6f-119">Indicates that the reason for non-equivalency is not known.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dfd6f-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dfd6f-120">Requirements</span></span>  
 <span data-ttu-id="dfd6f-121">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfd6f-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfd6f-122">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="dfd6f-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="dfd6f-123">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dfd6f-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dfd6f-124">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfd6f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfd6f-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="dfd6f-125">See also</span></span>

- [<span data-ttu-id="dfd6f-126">CompareAssemblyIdentity – funkce</span><span class="sxs-lookup"><span data-stu-id="dfd6f-126">CompareAssemblyIdentity Function</span></span>](compareassemblyidentity-function.md)
- [<span data-ttu-id="dfd6f-127">Výčty fúzí</span><span class="sxs-lookup"><span data-stu-id="dfd6f-127">Fusion Enumerations</span></span>](fusion-enumerations.md)
