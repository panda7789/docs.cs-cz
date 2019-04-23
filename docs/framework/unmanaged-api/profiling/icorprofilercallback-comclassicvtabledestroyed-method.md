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
ms.openlocfilehash: 63dc9ee81c98a23f01948a142018369eca7210b1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59116752"
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a><span data-ttu-id="45dd6-102">ICorProfilerCallback::COMClassicVTableDestroyed – metoda</span><span class="sxs-lookup"><span data-stu-id="45dd6-102">ICorProfilerCallback::COMClassicVTableDestroyed Method</span></span>
<span data-ttu-id="45dd6-103">Oznámí profileru, že se likviduje COM interop tabulku vtable.</span><span class="sxs-lookup"><span data-stu-id="45dd6-103">Notifies the profiler that a COM interop vtable is being destroyed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45dd6-104">Toto zpětné volání je nikdy mohou se vyskytnout, protože dochází ke zničení vtable velmi blízko vypnutí.</span><span class="sxs-lookup"><span data-stu-id="45dd6-104">This callback is likely never to occur, because the destruction of vtables occurs very close to shutdown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45dd6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45dd6-105">Syntax</span></span>  
  
```  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45dd6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="45dd6-106">Parameters</span></span>  
 `wrappedClasId`  
 <span data-ttu-id="45dd6-107">[in] ID třídy, pro který se vytvořil tento vtable.</span><span class="sxs-lookup"><span data-stu-id="45dd6-107">[in] The ID of the class for which this vtable was created.</span></span>  
  
 `implementedIID`  
 <span data-ttu-id="45dd6-108">[in] ID rozhraní implementované třídy.</span><span class="sxs-lookup"><span data-stu-id="45dd6-108">[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="45dd6-109">Tato hodnota může být NULL, pokud rozhraní je pouze interní.</span><span class="sxs-lookup"><span data-stu-id="45dd6-109">This value may be NULL if the interface is internal only.</span></span>  
  
 `pVTable`  
 <span data-ttu-id="45dd6-110">[in] Ukazatel na začátku tabulku vtable.</span><span class="sxs-lookup"><span data-stu-id="45dd6-110">[in] A pointer to the start of the vtable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45dd6-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="45dd6-111">Remarks</span></span>  
 <span data-ttu-id="45dd6-112">Profiler by neměla blokovat v rámci příslušné implementace této metody, protože zásobníku nemusí být ve stavu, která umožňuje uvolňování paměti, a proto není možné preemptive uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="45dd6-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="45dd6-113">Pokud profiler blokuje tady a dojde k pokusu o uvolnění paměti, modul runtime bude blokovat, dokud tento zpětného volání vrátí.</span><span class="sxs-lookup"><span data-stu-id="45dd6-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="45dd6-114">Okna profilování implementace této metody by neměla volat do spravovaného kódu nebo v jakékoli příčina způsob přidělení spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="45dd6-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45dd6-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="45dd6-115">Requirements</span></span>  
 <span data-ttu-id="45dd6-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45dd6-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45dd6-117">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="45dd6-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="45dd6-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45dd6-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45dd6-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45dd6-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45dd6-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="45dd6-120">See also</span></span>

- [<span data-ttu-id="45dd6-121">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45dd6-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="45dd6-122">COMClassicVTableCreated – metoda</span><span class="sxs-lookup"><span data-stu-id="45dd6-122">COMClassicVTableCreated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)
