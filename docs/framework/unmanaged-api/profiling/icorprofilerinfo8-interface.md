---
title: ICorProfilerInfo8 – rozhraní
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 476bcbd91188e3ff9eb63f50cfa2118a440b1a69
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868314"
---
# <a name="icorprofilerinfo8-interface"></a><span data-ttu-id="74ac1-102">ICorProfilerInfo8 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74ac1-102">ICorProfilerInfo8 Interface</span></span>

<span data-ttu-id="74ac1-103">Podtřída [ICorProfilerInfo7](icorprofilerinfo7-interface.md) , která poskytuje metody pro dotazování na informace o dynamických metodách.</span><span class="sxs-lookup"><span data-stu-id="74ac1-103">A subclass of [ICorProfilerInfo7](icorprofilerinfo7-interface.md) that provides methods to query information about dynamic methods.</span></span>

## <a name="methods"></a><span data-ttu-id="74ac1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="74ac1-104">Methods</span></span>  

| <span data-ttu-id="74ac1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="74ac1-105">Method</span></span>|<span data-ttu-id="74ac1-106">Popis</span><span class="sxs-lookup"><span data-stu-id="74ac1-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="74ac1-107">Metoda IsFunctionDynamic</span><span class="sxs-lookup"><span data-stu-id="74ac1-107">IsFunctionDynamic Method</span></span>](icorprofilerinfo8-isfunctiondynamic-method.md)| <span data-ttu-id="74ac1-108">Určuje, jestli funkce nemá přidružená metadata.</span><span class="sxs-lookup"><span data-stu-id="74ac1-108">Determines if a function does not have associated metadata.</span></span>|
|[<span data-ttu-id="74ac1-109">Metoda GetFunctionFromIP3</span><span class="sxs-lookup"><span data-stu-id="74ac1-109">GetFunctionFromIP3 Method</span></span>](icorprofilerinfo8-getfunctionfromip3-method.md)| <span data-ttu-id="74ac1-110">Mapuje ukazatel na instrukci spravovaného kódu na FunctionID.</span><span class="sxs-lookup"><span data-stu-id="74ac1-110">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="74ac1-111">Tato metoda spolupracuje s dynamickými i nedynamickými metodami.</span><span class="sxs-lookup"><span data-stu-id="74ac1-111">This method works for both dynamic and non-dynamic methods.</span></span> |
|[<span data-ttu-id="74ac1-112">Metoda GetDynamicFunctionInfo</span><span class="sxs-lookup"><span data-stu-id="74ac1-112">GetDynamicFunctionInfo Method</span></span>](icorprofilerinfo8-getdynamicfunctioninfo-method.md)| <span data-ttu-id="74ac1-113">Načte informace o dynamických metodách.</span><span class="sxs-lookup"><span data-stu-id="74ac1-113">Retrieves information about dynamic methods.</span></span> |

## <a name="requirements"></a><span data-ttu-id="74ac1-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="74ac1-114">Requirements</span></span>  
<span data-ttu-id="74ac1-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74ac1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="74ac1-116">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="74ac1-116">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="74ac1-117">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="74ac1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="74ac1-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74ac1-118">See also</span></span>

- [<span data-ttu-id="74ac1-119">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="74ac1-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
