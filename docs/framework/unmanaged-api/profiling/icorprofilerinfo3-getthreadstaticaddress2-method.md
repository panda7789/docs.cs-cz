---
title: ICorProfilerInfo3::GetThreadStaticAddress2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetThreadStaticAddress2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2
helpviewer_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2 method [.NET Framework profiling]
- GetThreadStaticAddress2 method [.NET Framework profiling]
ms.assetid: a9608861-ae64-4467-8a73-be05ad34beac
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 85f3ec6c2e0e452d3410437a7ec7cd45eb38cd5a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779852"
---
# <a name="icorprofilerinfo3getthreadstaticaddress2-method"></a><span data-ttu-id="84fb2-102">ICorProfilerInfo3::GetThreadStaticAddress2 – metoda</span><span class="sxs-lookup"><span data-stu-id="84fb2-102">ICorProfilerInfo3::GetThreadStaticAddress2 Method</span></span>
<span data-ttu-id="84fb2-103">Získá adresu zadané pole vlákna, která je v rámci zadaného vlákna a domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="84fb2-103">Gets the address of the specified thread-static field that is in the scope of the specified thread and application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84fb2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84fb2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStaticAddress2(  
                [in] ClassID classId,  
                [in] mdFieldDef fieldToken,  
                [in] AppDomainID appDomainId,  
                [in] ThreadID threadId,  
                [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84fb2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="84fb2-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="84fb2-106">[in] ID třídy, která obsahuje požadovaná pole statická na úrovni vlákna.</span><span class="sxs-lookup"><span data-stu-id="84fb2-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="84fb2-107">[in] Token metadat pro požadované pole statická na úrovni vlákna.</span><span class="sxs-lookup"><span data-stu-id="84fb2-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="84fb2-108">[in] ID domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="84fb2-108">[in] The ID of the application domain.</span></span>  
  
 `threadId`  
 <span data-ttu-id="84fb2-109">[in] ID vlákna, která je v oboru pro požadovaný statické pole.</span><span class="sxs-lookup"><span data-stu-id="84fb2-109">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="84fb2-110">[out] Ukazatel na adresu statické pole, která je v rámci zadaného vlákna.</span><span class="sxs-lookup"><span data-stu-id="84fb2-110">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84fb2-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="84fb2-111">Remarks</span></span>  
 <span data-ttu-id="84fb2-112">`GetThreadStaticAddress2` Metoda může vrátit jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="84fb2-112">The `GetThreadStaticAddress2` method may return one of the following:</span></span>  
  
- <span data-ttu-id="84fb2-113">CORPROF_E_DATAINCOMPLETE HRESULT, pokud daný statické pole nebyla přiřazena adresa v zadaném kontextu.</span><span class="sxs-lookup"><span data-stu-id="84fb2-113">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="84fb2-114">Adresy objektů, které mohou být v haldě uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="84fb2-114">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="84fb2-115">Tyto adresy mohou stát neplatnými po uvolnění paměti, takže po uvolnění paměti, profilovací programy by neměl se předpokládá, že jsou platné.</span><span class="sxs-lookup"><span data-stu-id="84fb2-115">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="84fb2-116">Před dokončením konstruktoru třídy třídy `GetThreadStaticAddress2` vrátí CORPROF_E_DATAINCOMPLETE pro všechny jeho statická pole, i když některé statická pole může již být inicializován a kořenová objekty uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="84fb2-116">Before a class’s class constructor is completed, `GetThreadStaticAddress2` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
 <span data-ttu-id="84fb2-117">[ICorProfilerInfo2::getthreadstaticaddress –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md) metoda je podobná `GetThreadStaticAddress2` metody, ale nepřijímá argument domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="84fb2-117">The [ICorProfilerInfo2::GetThreadStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md) method is similar to the `GetThreadStaticAddress2` method, but does not accept an application domain argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84fb2-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="84fb2-118">Requirements</span></span>  
 <span data-ttu-id="84fb2-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84fb2-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84fb2-120">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="84fb2-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="84fb2-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84fb2-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84fb2-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84fb2-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84fb2-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="84fb2-123">See also</span></span>

- [<span data-ttu-id="84fb2-124">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="84fb2-124">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="84fb2-125">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="84fb2-125">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="84fb2-126">Profilace</span><span class="sxs-lookup"><span data-stu-id="84fb2-126">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
