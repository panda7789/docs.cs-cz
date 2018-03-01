---
title: "ICorProfilerCallback::COMClassicVTableCreated – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback.COMClassicVTableCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::COMClassicVTableCreated
helpviewer_keywords:
- COMClassicVTableCreated method [.NET Framework profiling]
- ICorProfilerCallback::COMClassicVTableCreated method [.NET Framework profiling]
ms.assetid: 6e1834ab-c359-498a-b10b-984ae23cdda4
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 43fb447393e1d34ca53fbb62ecdc456a97452bc4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackcomclassicvtablecreated-method"></a><span data-ttu-id="1c3e5-102">ICorProfilerCallback::COMClassicVTableCreated – metoda</span><span class="sxs-lookup"><span data-stu-id="1c3e5-102">ICorProfilerCallback::COMClassicVTableCreated Method</span></span>
<span data-ttu-id="1c3e5-103">Vytvořený COM spolupráce tabulce vtable pro zadaný identifikátor IID a třída upozorní profileru.</span><span class="sxs-lookup"><span data-stu-id="1c3e5-103">Notifies the profiler that a COM interop vtable for the specified IID and class has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c3e5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c3e5-104">Syntax</span></span>  
  
```  
HRESULT COMClassicVTableCreated(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable,  
    [in] ULONG   cSlots);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1c3e5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1c3e5-105">Parameters</span></span>  
 `wrappedClasId`  
 <span data-ttu-id="1c3e5-106">[v] ID třídy, pro kterou byly vytvořeny tabulce vtable.</span><span class="sxs-lookup"><span data-stu-id="1c3e5-106">[in] The ID of the class for which the vtable has been created.</span></span>  
  
 `implementedIID`  
 <span data-ttu-id="1c3e5-107">[v] ID rozhraní implementované třídou.</span><span class="sxs-lookup"><span data-stu-id="1c3e5-107">[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="1c3e5-108">Tato hodnota může mít hodnotu NULL, pokud rozhraní je jenom interní.</span><span class="sxs-lookup"><span data-stu-id="1c3e5-108">This value may be NULL if the interface is internal only.</span></span>  
  
 `pVTable`  
 <span data-ttu-id="1c3e5-109">[v] Ukazatel na spuštění tabulce vtable.</span><span class="sxs-lookup"><span data-stu-id="1c3e5-109">[in] A pointer to the start of the vtable.</span></span>  
  
 `cSlots`  
 <span data-ttu-id="1c3e5-110">[v] Počet sloty, které jsou v tabulce vtable.</span><span class="sxs-lookup"><span data-stu-id="1c3e5-110">[in] The number of slots that are in the vtable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c3e5-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1c3e5-111">Remarks</span></span>  
 <span data-ttu-id="1c3e5-112">Profileru by neměly blokovat v jeho implementace této metody, protože zásobník nemusí být ve stavu, který umožňuje uvolňování paměti, a proto nelze povolit preemptivní uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="1c3e5-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="1c3e5-113">Pokud zde blokuje profileru a dojde k pokusu o uvolňování paměti, modul runtime se zablokuje, dokud se vrátí tato zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="1c3e5-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="1c3e5-114">Okna profilování implementace této metody by neměla volání do spravovaného kódu nebo v žádné příčina způsob přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="1c3e5-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c3e5-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1c3e5-115">Requirements</span></span>  
 <span data-ttu-id="1c3e5-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c3e5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c3e5-117">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1c3e5-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1c3e5-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c3e5-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c3e5-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c3e5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c3e5-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="1c3e5-120">See Also</span></span>  
 [<span data-ttu-id="1c3e5-121">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1c3e5-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="1c3e5-122">COMClassicVTableDestroyed – metoda</span><span class="sxs-lookup"><span data-stu-id="1c3e5-122">COMClassicVTableDestroyed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)
