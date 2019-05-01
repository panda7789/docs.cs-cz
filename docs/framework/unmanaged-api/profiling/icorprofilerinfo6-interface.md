---
title: ICorProfilerInfo6 Interface
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo6
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 6f2bb148-1e2b-4e45-a5a5-0ceddc40064b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: febe130b4d61b6179aeab3bfcd63891c38b13fbe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041116"
---
# <a name="icorprofilerinfo6-interface"></a><span data-ttu-id="d7535-102">ICorProfilerInfo6 Interface</span><span class="sxs-lookup"><span data-stu-id="d7535-102">ICorProfilerInfo6 Interface</span></span>
<span data-ttu-id="d7535-103">[Podporované v rozhraní .NET Framework 4.6 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="d7535-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="d7535-104">Podtřída [ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md) , který poskytuje enumerátor pro všechny metody, které jsou definovány v zadaném modulu NGen a vložené dané metody.</span><span class="sxs-lookup"><span data-stu-id="d7535-104">A subclass of [ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md) that provides an enumerator for all methods that are defined in a given NGen module and inline a given method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d7535-105">Metody</span><span class="sxs-lookup"><span data-stu-id="d7535-105">Methods</span></span>  
  
|<span data-ttu-id="d7535-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="d7535-106">Method</span></span>|<span data-ttu-id="d7535-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d7535-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d7535-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="d7535-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-enumngenmodulemethodsinliningthismethod-method.md)|<span data-ttu-id="d7535-109">Vrátí enumerátor pro všechny metody, která patří do daného modulu NGen a, které jsou vloženy do těla dané metody.</span><span class="sxs-lookup"><span data-stu-id="d7535-109">Returns an enumerator for all methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d7535-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d7535-110">Requirements</span></span>  
 <span data-ttu-id="d7535-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7535-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7535-112">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d7535-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d7535-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7535-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7535-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d7535-114">See also</span></span>

- [<span data-ttu-id="d7535-115">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="d7535-115">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
