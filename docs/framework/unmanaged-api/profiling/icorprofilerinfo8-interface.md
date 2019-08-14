---
title: Rozhraní ICorProfilerInfo8
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 210029ed1b1c7d780f3895f975f7a72227bbea80
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973693"
---
# <a name="icorprofilerinfo8-interface"></a><span data-ttu-id="c2395-102">Rozhraní ICorProfilerInfo8</span><span class="sxs-lookup"><span data-stu-id="c2395-102">ICorProfilerInfo8 Interface</span></span>

<span data-ttu-id="c2395-103">Podtřída [ICorProfilerInfo7](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) , která poskytuje metody pro dotazování na informace o dynamických metodách.</span><span class="sxs-lookup"><span data-stu-id="c2395-103">A subclass of [ICorProfilerInfo7](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) that provides methods to query information about dynamic methods.</span></span>

## <a name="methods"></a><span data-ttu-id="c2395-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c2395-104">Methods</span></span>  

| <span data-ttu-id="c2395-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c2395-105">Method</span></span>|<span data-ttu-id="c2395-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c2395-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="c2395-107">Metoda IsFunctionDynamic</span><span class="sxs-lookup"><span data-stu-id="c2395-107">IsFunctionDynamic Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-isfunctiondynamic-method.md)| <span data-ttu-id="c2395-108">Určuje, jestli funkce nemá přidružená metadata.</span><span class="sxs-lookup"><span data-stu-id="c2395-108">Determines if a function does not have associated metadata.</span></span>|
|[<span data-ttu-id="c2395-109">Metoda GetFunctionFromIP3</span><span class="sxs-lookup"><span data-stu-id="c2395-109">GetFunctionFromIP3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-getfunctionfromip3-method.md)| <span data-ttu-id="c2395-110">Mapuje ukazatel na instrukci spravovaného kódu na FunctionID.</span><span class="sxs-lookup"><span data-stu-id="c2395-110">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="c2395-111">Tato metoda spolupracuje s dynamickými i nedynamickými metodami.</span><span class="sxs-lookup"><span data-stu-id="c2395-111">This method works for both dynamic and non-dynamic methods.</span></span> |
|[<span data-ttu-id="c2395-112">Metoda GetDynamicFunctionInfo</span><span class="sxs-lookup"><span data-stu-id="c2395-112">GetDynamicFunctionInfo Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-getdynamicfunctioninfo-method.md)| <span data-ttu-id="c2395-113">Načte informace o dynamických metodách.</span><span class="sxs-lookup"><span data-stu-id="c2395-113">Retrieves information about dynamic methods.</span></span> |

## <a name="requirements"></a><span data-ttu-id="c2395-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c2395-114">Requirements</span></span>  
<span data-ttu-id="c2395-115">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2395-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="c2395-116">**Hlaviček** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c2395-116">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="c2395-117">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c2395-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
## <a name="see-also"></a><span data-ttu-id="c2395-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2395-118">See also</span></span>
- [<span data-ttu-id="c2395-119">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="c2395-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
