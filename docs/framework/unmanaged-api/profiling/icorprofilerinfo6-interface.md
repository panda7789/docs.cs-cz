---
title: ICorProfilerInfo6 rozhraní
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
ms.openlocfilehash: da1aab48e2eef229bb31e9443a5549c3f9fbc621
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455299"
---
# <a name="icorprofilerinfo6-interface"></a><span data-ttu-id="4205a-102">ICorProfilerInfo6 rozhraní</span><span class="sxs-lookup"><span data-stu-id="4205a-102">ICorProfilerInfo6 Interface</span></span>
<span data-ttu-id="4205a-103">[Podporované v rozhraní .NET Framework 4.6 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="4205a-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="4205a-104">Podtřídou třídy [ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md) poskytuje enumerátor pro všechny metody, které jsou definovány v daném modulu NGen a vložené dané metody.</span><span class="sxs-lookup"><span data-stu-id="4205a-104">A subclass of [ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md) that provides an enumerator for all methods that are defined in a given NGen module and inline a given method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4205a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4205a-105">Methods</span></span>  
  
|<span data-ttu-id="4205a-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="4205a-106">Method</span></span>|<span data-ttu-id="4205a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4205a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4205a-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="4205a-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-enumngenmodulemethodsinliningthismethod-method.md)|<span data-ttu-id="4205a-109">Vrátí enumerátor pro všechny metody, který patří k dané NGen modulu a které jsou vložená v těle dané metody.</span><span class="sxs-lookup"><span data-stu-id="4205a-109">Returns an enumerator for all methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4205a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4205a-110">Requirements</span></span>  
 <span data-ttu-id="4205a-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4205a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4205a-112">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4205a-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4205a-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4205a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4205a-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="4205a-114">See Also</span></span>  
 [<span data-ttu-id="4205a-115">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="4205a-115">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
