---
title: ICorProfilerCallback::COMClassicVTableCreated – metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: 808c26f53c4089248420280a43c88a1b3af0dad9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866543"
---
# <a name="icorprofilercallbackcomclassicvtablecreated-method"></a><span data-ttu-id="451e4-102">ICorProfilerCallback::COMClassicVTableCreated – metoda</span><span class="sxs-lookup"><span data-stu-id="451e4-102">ICorProfilerCallback::COMClassicVTableCreated Method</span></span>
<span data-ttu-id="451e4-103">Upozorní profileru, že se vytvořila tabulka zprostředkovatele komunikace s objekty COM pro zadaný identifikátor IID a třídu.</span><span class="sxs-lookup"><span data-stu-id="451e4-103">Notifies the profiler that a COM interop vtable for the specified IID and class has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="451e4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="451e4-104">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableCreated(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable,  
    [in] ULONG   cSlots);  
```  
  
## <a name="parameters"></a><span data-ttu-id="451e4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="451e4-105">Parameters</span></span>

- `wrappedClasId`

  <span data-ttu-id="451e4-106">\[v] ID třídy, pro kterou byl vytvořen vtable.</span><span class="sxs-lookup"><span data-stu-id="451e4-106">\[in] The ID of the class for which the vtable has been created.</span></span>

- `implementedIID`

  <span data-ttu-id="451e4-107">\[v] ID rozhraní implementovaného třídou.</span><span class="sxs-lookup"><span data-stu-id="451e4-107">\[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="451e4-108">Tato hodnota může být NULL, pokud je rozhraní pouze interní.</span><span class="sxs-lookup"><span data-stu-id="451e4-108">This value may be NULL if the interface is internal only.</span></span>

- `pVTable`

  <span data-ttu-id="451e4-109">\[in] ukazatel na začátek vtable.</span><span class="sxs-lookup"><span data-stu-id="451e4-109">\[in] A pointer to the start of the vtable.</span></span>

- `cSlots`

  <span data-ttu-id="451e4-110">\[v] počet slotů, které jsou v tabulce vtable.</span><span class="sxs-lookup"><span data-stu-id="451e4-110">\[in] The number of slots that are in the vtable.</span></span>

## <a name="remarks"></a><span data-ttu-id="451e4-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="451e4-111">Remarks</span></span>  
 <span data-ttu-id="451e4-112">Profiler by neměl při implementaci této metody blokovat, protože zásobník pravděpodobně není ve stavu, který umožňuje uvolňování paměti, a proto nelze povolit bezstavové uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="451e4-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="451e4-113">Pokud se tady zablokuje Profiler a dojde k pokusu o uvolnění paměti, modul runtime se zablokuje, dokud toto zpětné volání nevrátí.</span><span class="sxs-lookup"><span data-stu-id="451e4-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="451e4-114">Implementace této metody v profileru by se neměla volat do spravovaného kódu nebo jakýmkoli způsobem způsobovat alokaci spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="451e4-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="451e4-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="451e4-115">Requirements</span></span>  
 <span data-ttu-id="451e4-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="451e4-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="451e4-117">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="451e4-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="451e4-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="451e4-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="451e4-119">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="451e4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="451e4-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="451e4-120">See also</span></span>

- [<span data-ttu-id="451e4-121">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="451e4-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="451e4-122">COMClassicVTableDestroyed – metoda</span><span class="sxs-lookup"><span data-stu-id="451e4-122">COMClassicVTableDestroyed Method</span></span>](icorprofilercallback-comclassicvtabledestroyed-method.md)
