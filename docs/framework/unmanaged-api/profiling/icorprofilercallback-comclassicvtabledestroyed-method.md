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
ms.openlocfilehash: 0b0683d43778c4733b476e9feef459207b9d1ee6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445025"
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a><span data-ttu-id="a52b7-102">ICorProfilerCallback::COMClassicVTableDestroyed – metoda</span><span class="sxs-lookup"><span data-stu-id="a52b7-102">ICorProfilerCallback::COMClassicVTableDestroyed Method</span></span>
<span data-ttu-id="a52b7-103">Upozorní profileru, že je zničena tabulka zprostředkovatele komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="a52b7-103">Notifies the profiler that a COM interop vtable is being destroyed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a52b7-104">Toto zpětné volání se pravděpodobně nikdy nestane, protože zničení tabulek vtable je velmi blízko vypnutí.</span><span class="sxs-lookup"><span data-stu-id="a52b7-104">This callback is likely never to occur, because the destruction of vtables occurs very close to shutdown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a52b7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a52b7-105">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a52b7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a52b7-106">Parameters</span></span>  
 `wrappedClassId`  
 <span data-ttu-id="a52b7-107">pro ID třídy, pro kterou se vytvořila tabulka vtable</span><span class="sxs-lookup"><span data-stu-id="a52b7-107">[in] The ID of the class for which this vtable was created.</span></span>  
  
 `implementedIID`  
 <span data-ttu-id="a52b7-108">pro IDENTIFIKÁTOR rozhraní implementovaného třídou</span><span class="sxs-lookup"><span data-stu-id="a52b7-108">[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="a52b7-109">Tato hodnota může být NULL, pokud je rozhraní pouze interní.</span><span class="sxs-lookup"><span data-stu-id="a52b7-109">This value may be NULL if the interface is internal only.</span></span>  
  
 `pVTable`  
 <span data-ttu-id="a52b7-110">pro Ukazatel na začátek vtable.</span><span class="sxs-lookup"><span data-stu-id="a52b7-110">[in] A pointer to the start of the vtable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a52b7-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a52b7-111">Remarks</span></span>  
 <span data-ttu-id="a52b7-112">Profiler by neměl při implementaci této metody blokovat, protože zásobník pravděpodobně není ve stavu, který umožňuje uvolňování paměti, a proto nelze povolit bezstavové uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="a52b7-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="a52b7-113">Pokud se tady zablokuje Profiler a dojde k pokusu o uvolnění paměti, modul runtime se zablokuje, dokud toto zpětné volání nevrátí.</span><span class="sxs-lookup"><span data-stu-id="a52b7-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="a52b7-114">Implementace této metody v profileru by se neměla volat do spravovaného kódu nebo jakýmkoli způsobem způsobovat alokaci spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="a52b7-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a52b7-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a52b7-115">Requirements</span></span>  
 <span data-ttu-id="a52b7-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a52b7-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a52b7-117">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a52b7-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a52b7-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a52b7-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a52b7-119">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a52b7-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a52b7-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a52b7-120">See also</span></span>

- [<span data-ttu-id="a52b7-121">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a52b7-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="a52b7-122">COMClassicVTableCreated – metoda</span><span class="sxs-lookup"><span data-stu-id="a52b7-122">COMClassicVTableCreated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)
