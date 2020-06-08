---
title: ICorProfilerInfo8 – rozhraní
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 2cca915eda44d73aea7469e5f752c57309c2300d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495161"
---
# <a name="icorprofilerinfo8-interface"></a><span data-ttu-id="be2cd-102">ICorProfilerInfo8 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="be2cd-102">ICorProfilerInfo8 Interface</span></span>

<span data-ttu-id="be2cd-103">Podtřída [ICorProfilerInfo7](icorprofilerinfo7-interface.md) , která poskytuje metody pro dotazování na informace o dynamických metodách.</span><span class="sxs-lookup"><span data-stu-id="be2cd-103">A subclass of [ICorProfilerInfo7](icorprofilerinfo7-interface.md) that provides methods to query information about dynamic methods.</span></span>

## <a name="methods"></a><span data-ttu-id="be2cd-104">Metody</span><span class="sxs-lookup"><span data-stu-id="be2cd-104">Methods</span></span>  

| <span data-ttu-id="be2cd-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="be2cd-105">Method</span></span>|<span data-ttu-id="be2cd-106">Description</span><span class="sxs-lookup"><span data-stu-id="be2cd-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="be2cd-107">IsFunctionDynamic – metoda</span><span class="sxs-lookup"><span data-stu-id="be2cd-107">IsFunctionDynamic Method</span></span>](icorprofilerinfo8-isfunctiondynamic-method.md)| <span data-ttu-id="be2cd-108">Určuje, jestli funkce nemá přidružená metadata.</span><span class="sxs-lookup"><span data-stu-id="be2cd-108">Determines if a function does not have associated metadata.</span></span>|
|[<span data-ttu-id="be2cd-109">GetFunctionFromIP3 – metoda</span><span class="sxs-lookup"><span data-stu-id="be2cd-109">GetFunctionFromIP3 Method</span></span>](icorprofilerinfo8-getfunctionfromip3-method.md)| <span data-ttu-id="be2cd-110">Mapuje ukazatel na instrukci spravovaného kódu na FunctionID.</span><span class="sxs-lookup"><span data-stu-id="be2cd-110">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="be2cd-111">Tato metoda spolupracuje s dynamickými i nedynamickými metodami.</span><span class="sxs-lookup"><span data-stu-id="be2cd-111">This method works for both dynamic and non-dynamic methods.</span></span> |
|[<span data-ttu-id="be2cd-112">GetDynamicFunctionInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="be2cd-112">GetDynamicFunctionInfo Method</span></span>](icorprofilerinfo8-getdynamicfunctioninfo-method.md)| <span data-ttu-id="be2cd-113">Načte informace o dynamických metodách.</span><span class="sxs-lookup"><span data-stu-id="be2cd-113">Retrieves information about dynamic methods.</span></span> |

## <a name="requirements"></a><span data-ttu-id="be2cd-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="be2cd-114">Requirements</span></span>  
<span data-ttu-id="be2cd-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be2cd-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="be2cd-116">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="be2cd-116">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="be2cd-117">**Verze .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="be2cd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="be2cd-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="be2cd-118">See also</span></span>

- [<span data-ttu-id="be2cd-119">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="be2cd-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
