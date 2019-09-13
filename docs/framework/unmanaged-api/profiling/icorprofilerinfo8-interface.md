---
title: ICorProfilerInfo8 – rozhraní
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 2baa33a7a3527392d8095b5d0ec7ad6af8a71a8e
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928940"
---
# <a name="icorprofilerinfo8-interface"></a><span data-ttu-id="a2b97-102">ICorProfilerInfo8 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a2b97-102">ICorProfilerInfo8 Interface</span></span>

<span data-ttu-id="a2b97-103">Podtřída [ICorProfilerInfo7](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) , která poskytuje metody pro dotazování na informace o dynamických metodách.</span><span class="sxs-lookup"><span data-stu-id="a2b97-103">A subclass of [ICorProfilerInfo7](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) that provides methods to query information about dynamic methods.</span></span>

## <a name="methods"></a><span data-ttu-id="a2b97-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a2b97-104">Methods</span></span>  

| <span data-ttu-id="a2b97-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a2b97-105">Method</span></span>|<span data-ttu-id="a2b97-106">Popis</span><span class="sxs-lookup"><span data-stu-id="a2b97-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="a2b97-107">Metoda IsFunctionDynamic</span><span class="sxs-lookup"><span data-stu-id="a2b97-107">IsFunctionDynamic Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-isfunctiondynamic-method.md)| <span data-ttu-id="a2b97-108">Určuje, jestli funkce nemá přidružená metadata.</span><span class="sxs-lookup"><span data-stu-id="a2b97-108">Determines if a function does not have associated metadata.</span></span>|
|[<span data-ttu-id="a2b97-109">Metoda GetFunctionFromIP3</span><span class="sxs-lookup"><span data-stu-id="a2b97-109">GetFunctionFromIP3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-getfunctionfromip3-method.md)| <span data-ttu-id="a2b97-110">Mapuje ukazatel na instrukci spravovaného kódu na FunctionID.</span><span class="sxs-lookup"><span data-stu-id="a2b97-110">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="a2b97-111">Tato metoda spolupracuje s dynamickými i nedynamickými metodami.</span><span class="sxs-lookup"><span data-stu-id="a2b97-111">This method works for both dynamic and non-dynamic methods.</span></span> |
|[<span data-ttu-id="a2b97-112">Metoda GetDynamicFunctionInfo</span><span class="sxs-lookup"><span data-stu-id="a2b97-112">GetDynamicFunctionInfo Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-getdynamicfunctioninfo-method.md)| <span data-ttu-id="a2b97-113">Načte informace o dynamických metodách.</span><span class="sxs-lookup"><span data-stu-id="a2b97-113">Retrieves information about dynamic methods.</span></span> |

## <a name="requirements"></a><span data-ttu-id="a2b97-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a2b97-114">Requirements</span></span>  
<span data-ttu-id="a2b97-115">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2b97-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="a2b97-116">**Hlaviček** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a2b97-116">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="a2b97-117">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a2b97-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="a2b97-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a2b97-118">See also</span></span>

- [<span data-ttu-id="a2b97-119">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="a2b97-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
