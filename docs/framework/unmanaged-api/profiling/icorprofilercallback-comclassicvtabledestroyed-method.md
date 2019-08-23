---
title: ICorProfilerCallback::COMClassicVTableDestroyed – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.COMClassicVTableDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed
helpviewer_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed method [.NET Framework profiling]
- COMClassicVTableDestroyed method [.NET Framework profiling]
ms.assetid: 29da20ca-bf39-4356-8099-d9c3ac3423a9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f74e06ea4cb4d7a8eace8c7852f487bbdcbcd875
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964629"
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a><span data-ttu-id="87ba6-102">ICorProfilerCallback::COMClassicVTableDestroyed – metoda</span><span class="sxs-lookup"><span data-stu-id="87ba6-102">ICorProfilerCallback::COMClassicVTableDestroyed Method</span></span>
<span data-ttu-id="87ba6-103">Upozorní profileru, že je zničena tabulka zprostředkovatele komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="87ba6-103">Notifies the profiler that a COM interop vtable is being destroyed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="87ba6-104">Toto zpětné volání se pravděpodobně nikdy nestane, protože zničení tabulek vtable je velmi blízko vypnutí.</span><span class="sxs-lookup"><span data-stu-id="87ba6-104">This callback is likely never to occur, because the destruction of vtables occurs very close to shutdown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87ba6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87ba6-105">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87ba6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="87ba6-106">Parameters</span></span>  
 `wrappedClassId`  
 <span data-ttu-id="87ba6-107">pro ID třídy, pro kterou se vytvořila tabulka vtable</span><span class="sxs-lookup"><span data-stu-id="87ba6-107">[in] The ID of the class for which this vtable was created.</span></span>  
  
 `implementedIID`  
 <span data-ttu-id="87ba6-108">pro IDENTIFIKÁTOR rozhraní implementovaného třídou</span><span class="sxs-lookup"><span data-stu-id="87ba6-108">[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="87ba6-109">Tato hodnota může být NULL, pokud je rozhraní pouze interní.</span><span class="sxs-lookup"><span data-stu-id="87ba6-109">This value may be NULL if the interface is internal only.</span></span>  
  
 `pVTable`  
 <span data-ttu-id="87ba6-110">pro Ukazatel na začátek vtable.</span><span class="sxs-lookup"><span data-stu-id="87ba6-110">[in] A pointer to the start of the vtable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87ba6-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="87ba6-111">Remarks</span></span>  
 <span data-ttu-id="87ba6-112">Profiler by neměl při implementaci této metody blokovat, protože zásobník pravděpodobně není ve stavu, který umožňuje uvolňování paměti, a proto nelze povolit bezstavové uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="87ba6-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="87ba6-113">Pokud se tady zablokuje Profiler a dojde k pokusu o uvolnění paměti, modul runtime se zablokuje, dokud toto zpětné volání nevrátí.</span><span class="sxs-lookup"><span data-stu-id="87ba6-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="87ba6-114">Implementace této metody v profileru by se neměla volat do spravovaného kódu nebo jakýmkoli způsobem způsobovat alokaci spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="87ba6-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87ba6-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="87ba6-115">Requirements</span></span>  
 <span data-ttu-id="87ba6-116">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87ba6-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87ba6-117">**Hlaviček** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="87ba6-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="87ba6-118">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87ba6-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87ba6-119">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87ba6-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87ba6-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="87ba6-120">See also</span></span>

- [<span data-ttu-id="87ba6-121">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="87ba6-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="87ba6-122">COMClassicVTableCreated – metoda</span><span class="sxs-lookup"><span data-stu-id="87ba6-122">COMClassicVTableCreated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)
