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
ms.openlocfilehash: 4aa11b036c64ff6ffeec583c4cdd818d26067a74
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598243"
---
# <a name="icorprofilercallbackcomclassicvtablecreated-method"></a><span data-ttu-id="b99a7-102">ICorProfilerCallback::COMClassicVTableCreated – metoda</span><span class="sxs-lookup"><span data-stu-id="b99a7-102">ICorProfilerCallback::COMClassicVTableCreated Method</span></span>
<span data-ttu-id="b99a7-103">Oznámí profileru, že se vytvořila COM interop tabulku vtable pro zadaný identifikátor IID a třídy.</span><span class="sxs-lookup"><span data-stu-id="b99a7-103">Notifies the profiler that a COM interop vtable for the specified IID and class has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b99a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b99a7-104">Syntax</span></span>  
  
```  
HRESULT COMClassicVTableCreated(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable,  
    [in] ULONG   cSlots);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b99a7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b99a7-105">Parameters</span></span>  
 `wrappedClasId`  
 <span data-ttu-id="b99a7-106">[in] ID třídy, pro kterou byly vytvořeny tabulce vtable.</span><span class="sxs-lookup"><span data-stu-id="b99a7-106">[in] The ID of the class for which the vtable has been created.</span></span>  
  
 `implementedIID`  
 <span data-ttu-id="b99a7-107">[in] ID rozhraní implementované třídy.</span><span class="sxs-lookup"><span data-stu-id="b99a7-107">[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="b99a7-108">Tato hodnota může být NULL, pokud rozhraní je pouze interní.</span><span class="sxs-lookup"><span data-stu-id="b99a7-108">This value may be NULL if the interface is internal only.</span></span>  
  
 `pVTable`  
 <span data-ttu-id="b99a7-109">[in] Ukazatel na začátku tabulku vtable.</span><span class="sxs-lookup"><span data-stu-id="b99a7-109">[in] A pointer to the start of the vtable.</span></span>  
  
 `cSlots`  
 <span data-ttu-id="b99a7-110">[in] Počet slotů, které jsou v tabulce vtable.</span><span class="sxs-lookup"><span data-stu-id="b99a7-110">[in] The number of slots that are in the vtable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b99a7-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b99a7-111">Remarks</span></span>  
 <span data-ttu-id="b99a7-112">Profiler by neměla blokovat v rámci příslušné implementace této metody, protože zásobníku nemusí být ve stavu, která umožňuje uvolňování paměti, a proto není možné preemptive uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b99a7-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="b99a7-113">Pokud profiler blokuje tady a dojde k pokusu o uvolnění paměti, modul runtime bude blokovat, dokud tento zpětného volání vrátí.</span><span class="sxs-lookup"><span data-stu-id="b99a7-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="b99a7-114">Okna profilování implementace této metody by neměla volat do spravovaného kódu nebo v jakékoli příčina způsob přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="b99a7-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b99a7-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b99a7-115">Requirements</span></span>  
 <span data-ttu-id="b99a7-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b99a7-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b99a7-117">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b99a7-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b99a7-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b99a7-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b99a7-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b99a7-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b99a7-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b99a7-120">See also</span></span>

- [<span data-ttu-id="b99a7-121">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b99a7-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="b99a7-122">COMClassicVTableDestroyed – metoda</span><span class="sxs-lookup"><span data-stu-id="b99a7-122">COMClassicVTableDestroyed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)
