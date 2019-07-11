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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 062b63776264ae553039a2db0fc99d4fb7bec476
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745336"
---
# <a name="icorprofilercallbackcomclassicvtablecreated-method"></a><span data-ttu-id="05db4-102">ICorProfilerCallback::COMClassicVTableCreated – metoda</span><span class="sxs-lookup"><span data-stu-id="05db4-102">ICorProfilerCallback::COMClassicVTableCreated Method</span></span>
<span data-ttu-id="05db4-103">Oznámí profileru, že se vytvořila COM interop tabulku vtable pro zadaný identifikátor IID a třídy.</span><span class="sxs-lookup"><span data-stu-id="05db4-103">Notifies the profiler that a COM interop vtable for the specified IID and class has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05db4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05db4-104">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableCreated(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable,  
    [in] ULONG   cSlots);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05db4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="05db4-105">Parameters</span></span>  
 `wrappedClasId`  
 <span data-ttu-id="05db4-106">[in] ID třídy, pro kterou byly vytvořeny tabulce vtable.</span><span class="sxs-lookup"><span data-stu-id="05db4-106">[in] The ID of the class for which the vtable has been created.</span></span>  
  
 `implementedIID`  
 <span data-ttu-id="05db4-107">[in] ID rozhraní implementované třídy.</span><span class="sxs-lookup"><span data-stu-id="05db4-107">[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="05db4-108">Tato hodnota může být NULL, pokud rozhraní je pouze interní.</span><span class="sxs-lookup"><span data-stu-id="05db4-108">This value may be NULL if the interface is internal only.</span></span>  
  
 `pVTable`  
 <span data-ttu-id="05db4-109">[in] Ukazatel na začátku tabulku vtable.</span><span class="sxs-lookup"><span data-stu-id="05db4-109">[in] A pointer to the start of the vtable.</span></span>  
  
 `cSlots`  
 <span data-ttu-id="05db4-110">[in] Počet slotů, které jsou v tabulce vtable.</span><span class="sxs-lookup"><span data-stu-id="05db4-110">[in] The number of slots that are in the vtable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05db4-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="05db4-111">Remarks</span></span>  
 <span data-ttu-id="05db4-112">Profiler by neměla blokovat v rámci příslušné implementace této metody, protože zásobníku nemusí být ve stavu, která umožňuje uvolňování paměti, a proto není možné preemptive uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="05db4-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="05db4-113">Pokud profiler blokuje tady a dojde k pokusu o uvolnění paměti, modul runtime bude blokovat, dokud tento zpětného volání vrátí.</span><span class="sxs-lookup"><span data-stu-id="05db4-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="05db4-114">Okna profilování implementace této metody by neměla volat do spravovaného kódu nebo v jakékoli příčina způsob přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="05db4-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05db4-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="05db4-115">Requirements</span></span>  
 <span data-ttu-id="05db4-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05db4-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05db4-117">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="05db4-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="05db4-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05db4-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05db4-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05db4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05db4-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="05db4-120">See also</span></span>

- [<span data-ttu-id="05db4-121">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05db4-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="05db4-122">COMClassicVTableDestroyed – metoda</span><span class="sxs-lookup"><span data-stu-id="05db4-122">COMClassicVTableDestroyed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)
