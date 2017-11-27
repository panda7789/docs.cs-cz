---
title: "ICorProfilerCallback::COMClassicVTableDestroyed – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.COMClassicVTableDestroyed
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::COMClassicVTableDestroyed
helpviewer_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed method [.NET Framework profiling]
- COMClassicVTableDestroyed method [.NET Framework profiling]
ms.assetid: 29da20ca-bf39-4356-8099-d9c3ac3423a9
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ebff8297a708b130a0d3983fd75b76c3aeaeceaf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a><span data-ttu-id="dd3a3-102">ICorProfilerCallback::COMClassicVTableDestroyed – metoda</span><span class="sxs-lookup"><span data-stu-id="dd3a3-102">ICorProfilerCallback::COMClassicVTableDestroyed Method</span></span>
<span data-ttu-id="dd3a3-103">Upozorní profileru zničena vtable zprostředkovatele komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="dd3a3-103">Notifies the profiler that a COM interop vtable is being destroyed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dd3a3-104">Tento zpětného volání je může nikdy dojít, protože zničení virtuálních tabulek dojde k velmi brzy bude dosaženo vypnutí.</span><span class="sxs-lookup"><span data-stu-id="dd3a3-104">This callback is likely never to occur, because the destruction of vtables occurs very close to shutdown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd3a3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd3a3-105">Syntax</span></span>  
  
```  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dd3a3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="dd3a3-106">Parameters</span></span>  
 `wrappedClasId`  
 <span data-ttu-id="dd3a3-107">[v] ID třídy, pro který byl vytvořen tento vtable.</span><span class="sxs-lookup"><span data-stu-id="dd3a3-107">[in] The ID of the class for which this vtable was created.</span></span>  
  
 `implementedIID`  
 <span data-ttu-id="dd3a3-108">[v] ID rozhraní implementované třídou.</span><span class="sxs-lookup"><span data-stu-id="dd3a3-108">[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="dd3a3-109">Tato hodnota může mít hodnotu NULL, pokud rozhraní je jenom interní.</span><span class="sxs-lookup"><span data-stu-id="dd3a3-109">This value may be NULL if the interface is internal only.</span></span>  
  
 `pVTable`  
 <span data-ttu-id="dd3a3-110">[v] Ukazatel na spuštění tabulce vtable.</span><span class="sxs-lookup"><span data-stu-id="dd3a3-110">[in] A pointer to the start of the vtable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd3a3-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dd3a3-111">Remarks</span></span>  
 <span data-ttu-id="dd3a3-112">Profileru by neměly blokovat v jeho implementace této metody, protože zásobník nemusí být ve stavu, který umožňuje uvolňování paměti, a proto nelze povolit preemptivní uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="dd3a3-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="dd3a3-113">Pokud zde blokuje profileru a dojde k pokusu o uvolňování paměti, modul runtime se zablokuje, dokud se vrátí tato zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="dd3a3-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="dd3a3-114">Okna profilování implementace této metody by neměla volání do spravovaného kódu nebo v žádné příčina způsob přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="dd3a3-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd3a3-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dd3a3-115">Requirements</span></span>  
 <span data-ttu-id="dd3a3-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd3a3-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd3a3-117">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dd3a3-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dd3a3-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd3a3-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd3a3-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd3a3-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd3a3-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="dd3a3-120">See Also</span></span>  
 [<span data-ttu-id="dd3a3-121">Icorprofilercallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dd3a3-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="dd3a3-122">Comclassicvtablecreated – metoda</span><span class="sxs-lookup"><span data-stu-id="dd3a3-122">COMClassicVTableCreated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)
