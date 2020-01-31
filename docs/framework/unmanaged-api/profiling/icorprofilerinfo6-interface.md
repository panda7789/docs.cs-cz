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
ms.openlocfilehash: 80ac17a96e5c1c8c32cfc336da6c2be30eaf80fd
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868366"
---
# <a name="icorprofilerinfo6-interface"></a><span data-ttu-id="4c7f0-102">ICorProfilerInfo6 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4c7f0-102">ICorProfilerInfo6 Interface</span></span>
<span data-ttu-id="4c7f0-103">[Podporováno v .NET Framework 4,6 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="4c7f0-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="4c7f0-104">Podtřída [ICorProfilerInfo5](icorprofilerinfo5-interface.md) , která poskytuje enumerátor pro všechny metody, které jsou definovány v daném modulu Ngen a vloženy danou metodu.</span><span class="sxs-lookup"><span data-stu-id="4c7f0-104">A subclass of [ICorProfilerInfo5](icorprofilerinfo5-interface.md) that provides an enumerator for all methods that are defined in a given NGen module and inline a given method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4c7f0-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4c7f0-105">Methods</span></span>  
  
|<span data-ttu-id="4c7f0-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="4c7f0-106">Method</span></span>|<span data-ttu-id="4c7f0-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4c7f0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4c7f0-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="4c7f0-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>](icorprofilerinfo6-enumngenmodulemethodsinliningthismethod-method.md)|<span data-ttu-id="4c7f0-109">Vrátí enumerátor pro všechny metody, které patří do daného modulu NGen a které jsou vloženy v těle dané metody.</span><span class="sxs-lookup"><span data-stu-id="4c7f0-109">Returns an enumerator for all methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4c7f0-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4c7f0-110">Requirements</span></span>  
 <span data-ttu-id="4c7f0-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c7f0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c7f0-112">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4c7f0-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4c7f0-113">**Verze .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c7f0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c7f0-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4c7f0-114">See also</span></span>

- [<span data-ttu-id="4c7f0-115">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="4c7f0-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
