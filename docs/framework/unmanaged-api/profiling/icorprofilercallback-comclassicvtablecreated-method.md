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
ms.openlocfilehash: 6c9ec6af90cc47c3c01621563a9813789c25aa1d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500335"
---
# <a name="icorprofilercallbackcomclassicvtablecreated-method"></a><span data-ttu-id="3971b-102">ICorProfilerCallback::COMClassicVTableCreated – metoda</span><span class="sxs-lookup"><span data-stu-id="3971b-102">ICorProfilerCallback::COMClassicVTableCreated Method</span></span>
<span data-ttu-id="3971b-103">Upozorní profileru, že se vytvořila tabulka zprostředkovatele komunikace s objekty COM pro zadaný identifikátor IID a třídu.</span><span class="sxs-lookup"><span data-stu-id="3971b-103">Notifies the profiler that a COM interop vtable for the specified IID and class has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3971b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3971b-104">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableCreated(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable,  
    [in] ULONG   cSlots);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3971b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3971b-105">Parameters</span></span>

- `wrappedClasId`

  <span data-ttu-id="3971b-106">\[v] ID třídy, pro kterou byl vytvořen vtable.</span><span class="sxs-lookup"><span data-stu-id="3971b-106">\[in] The ID of the class for which the vtable has been created.</span></span>

- `implementedIID`

  <span data-ttu-id="3971b-107">\[v] ID rozhraní implementovaného třídou.</span><span class="sxs-lookup"><span data-stu-id="3971b-107">\[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="3971b-108">Tato hodnota může být NULL, pokud je rozhraní pouze interní.</span><span class="sxs-lookup"><span data-stu-id="3971b-108">This value may be NULL if the interface is internal only.</span></span>

- `pVTable`

  <span data-ttu-id="3971b-109">\[in] ukazatel na začátek vtable.</span><span class="sxs-lookup"><span data-stu-id="3971b-109">\[in] A pointer to the start of the vtable.</span></span>

- `cSlots`

  <span data-ttu-id="3971b-110">\[in] počet slotů, které jsou v tabulce vtable.</span><span class="sxs-lookup"><span data-stu-id="3971b-110">\[in] The number of slots that are in the vtable.</span></span>

## <a name="remarks"></a><span data-ttu-id="3971b-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3971b-111">Remarks</span></span>  
 <span data-ttu-id="3971b-112">Profiler by neměl při implementaci této metody blokovat, protože zásobník pravděpodobně není ve stavu, který umožňuje uvolňování paměti, a proto nelze povolit bezstavové uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="3971b-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="3971b-113">Pokud se tady zablokuje Profiler a dojde k pokusu o uvolnění paměti, modul runtime se zablokuje, dokud toto zpětné volání nevrátí.</span><span class="sxs-lookup"><span data-stu-id="3971b-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="3971b-114">Implementace této metody v profileru by se neměla volat do spravovaného kódu nebo jakýmkoli způsobem způsobovat alokaci spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="3971b-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3971b-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3971b-115">Requirements</span></span>  
 <span data-ttu-id="3971b-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3971b-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3971b-117">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3971b-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3971b-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3971b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3971b-119">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3971b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3971b-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3971b-120">See also</span></span>

- [<span data-ttu-id="3971b-121">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3971b-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="3971b-122">COMClassicVTableDestroyed – metoda</span><span class="sxs-lookup"><span data-stu-id="3971b-122">COMClassicVTableDestroyed Method</span></span>](icorprofilercallback-comclassicvtabledestroyed-method.md)
