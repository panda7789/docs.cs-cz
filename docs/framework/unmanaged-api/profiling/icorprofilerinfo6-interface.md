---
title: ICorProfilerInfo6 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo6
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 6f2bb148-1e2b-4e45-a5a5-0ceddc40064b
ms.openlocfilehash: fba57a88cd3af582b4edf0e5bdbf6ac48020c9f7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495501"
---
# <a name="icorprofilerinfo6-interface"></a><span data-ttu-id="01b5f-102">ICorProfilerInfo6 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01b5f-102">ICorProfilerInfo6 Interface</span></span>
<span data-ttu-id="01b5f-103">[Podporováno v .NET Framework 4,6 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="01b5f-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="01b5f-104">Podtřída [ICorProfilerInfo5](icorprofilerinfo5-interface.md) , která poskytuje enumerátor pro všechny metody, které jsou definovány v daném modulu Ngen a vloženy danou metodu.</span><span class="sxs-lookup"><span data-stu-id="01b5f-104">A subclass of [ICorProfilerInfo5](icorprofilerinfo5-interface.md) that provides an enumerator for all methods that are defined in a given NGen module and inline a given method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="01b5f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="01b5f-105">Methods</span></span>  
  
|<span data-ttu-id="01b5f-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="01b5f-106">Method</span></span>|<span data-ttu-id="01b5f-107">Description</span><span class="sxs-lookup"><span data-stu-id="01b5f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="01b5f-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="01b5f-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>](icorprofilerinfo6-enumngenmodulemethodsinliningthismethod-method.md)|<span data-ttu-id="01b5f-109">Vrátí enumerátor pro všechny metody, které patří do daného modulu NGen a které jsou vloženy v těle dané metody.</span><span class="sxs-lookup"><span data-stu-id="01b5f-109">Returns an enumerator for all methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="01b5f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="01b5f-110">Requirements</span></span>  
 <span data-ttu-id="01b5f-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01b5f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01b5f-112">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="01b5f-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="01b5f-113">**Verze .NET Framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01b5f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01b5f-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01b5f-114">See also</span></span>

- [<span data-ttu-id="01b5f-115">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="01b5f-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
