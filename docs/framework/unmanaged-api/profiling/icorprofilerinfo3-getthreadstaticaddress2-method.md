---
title: "ICorProfilerInfo3::GetThreadStaticAddress2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.GetThreadStaticAddress2 Method
api_location: Mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::GetThreadStaticAddress2
helpviewer_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2 method [.NET Framework profiling]
- GetThreadStaticAddress2 method [.NET Framework profiling]
ms.assetid: a9608861-ae64-4467-8a73-be05ad34beac
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 136b68f886899430dbfc672b8e3e534d093bc617
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3getthreadstaticaddress2-method"></a><span data-ttu-id="84906-102">ICorProfilerInfo3::GetThreadStaticAddress2 – metoda</span><span class="sxs-lookup"><span data-stu-id="84906-102">ICorProfilerInfo3::GetThreadStaticAddress2 Method</span></span>
<span data-ttu-id="84906-103">Získá adresu zadaného pole statické přístup z více vláken, který je v oboru zadaný vláken a domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="84906-103">Gets the address of the specified thread-static field that is in the scope of the specified thread and application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84906-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84906-104">Syntax</span></span>  
  
```  
HRESULT GetThreadStaticAddress2(  
                [in] ClassID classId,  
                [in] mdFieldDef fieldToken,  
                [in] AppDomainID appDomainId,  
                [in] ThreadID threadId,  
                [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="84906-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="84906-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="84906-106">[v] ID třídy, která obsahuje požadovaná pole statické přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="84906-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="84906-107">[v] Token metadata pro požadované pole statické přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="84906-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="84906-108">[v] ID domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="84906-108">[in] The ID of the application domain.</span></span>  
  
 `threadId`  
 <span data-ttu-id="84906-109">[v] ID podprocesu, který je v rozsahu pro požadovaný statické pole.</span><span class="sxs-lookup"><span data-stu-id="84906-109">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="84906-110">[out] Ukazatel na adresu statické pole, které je v rámci zadaného vlákno.</span><span class="sxs-lookup"><span data-stu-id="84906-110">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84906-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="84906-111">Remarks</span></span>  
 <span data-ttu-id="84906-112">`GetThreadStaticAddress2` Metoda může vrátit jednu z následujících:</span><span class="sxs-lookup"><span data-stu-id="84906-112">The `GetThreadStaticAddress2` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="84906-113">HRESULT CORPROF_E_DATAINCOMPLETE, pokud daný statické pole nebyla přiřazena adresu v zadaném kontextu.</span><span class="sxs-lookup"><span data-stu-id="84906-113">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="84906-114">Adresy objekty, které mohou být v kolekci halda paměti.</span><span class="sxs-lookup"><span data-stu-id="84906-114">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="84906-115">Tyto adresy může zneplatní po uvolňování paměti, takže po uvolnění paměti by neměl profilery předpokládá platnými.</span><span class="sxs-lookup"><span data-stu-id="84906-115">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="84906-116">Před dokončením konstruktoru třídy třídy `GetThreadStaticAddress2` vrátí CORPROF_E_DATAINCOMPLETE pro všechna její statické pole, i když některé statických polí mohou již být inicializován a vytvoření kořenového adresáře objekty kolekce paměti.</span><span class="sxs-lookup"><span data-stu-id="84906-116">Before a class’s class constructor is completed, `GetThreadStaticAddress2` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
 <span data-ttu-id="84906-117">[ICorProfilerInfo2::getthreadstaticaddress –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md) metoda je podobná `GetThreadStaticAddress2` metoda, ale nepřijímá argument domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="84906-117">The [ICorProfilerInfo2::GetThreadStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md) method is similar to the `GetThreadStaticAddress2` method, but does not accept an application domain argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84906-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="84906-118">Requirements</span></span>  
 <span data-ttu-id="84906-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84906-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84906-120">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="84906-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="84906-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84906-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84906-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84906-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84906-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="84906-123">See Also</span></span>  
 [<span data-ttu-id="84906-124">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="84906-124">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="84906-125">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="84906-125">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="84906-126">Profilace</span><span class="sxs-lookup"><span data-stu-id="84906-126">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
