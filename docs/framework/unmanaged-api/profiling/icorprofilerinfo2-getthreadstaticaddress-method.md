---
title: ICorProfilerInfo2::GetThreadStaticAddress – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetThreadStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetThreadStaticAddress
helpviewer_keywords:
- GetThreadStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetThreadStaticAddress method [.NET Framework profiling]
ms.assetid: 8e7dbf14-98a2-4384-a950-58a7640e59df
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a38c8323157cee866ac0ecab97532b9b72a932b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454123"
---
# <a name="icorprofilerinfo2getthreadstaticaddress-method"></a><span data-ttu-id="8509a-102">ICorProfilerInfo2::GetThreadStaticAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="8509a-102">ICorProfilerInfo2::GetThreadStaticAddress Method</span></span>
<span data-ttu-id="8509a-103">Získá adresu zadaného pole statické přístup z více vláken, který je v rozsahu zadaný vlákno.</span><span class="sxs-lookup"><span data-stu-id="8509a-103">Gets the address of the specified thread-static field that is in the scope of the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8509a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8509a-104">Syntax</span></span>  
  
```  
HRESULT GetThreadStaticAddress(  
    [in] ClassID     classId,  
    [in] mdFieldDef  fieldToken,  
    [in] ThreadID    threadId,  
    [out] void       **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8509a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8509a-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="8509a-106">[v] ID třídy, která obsahuje požadovaná pole statické přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="8509a-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="8509a-107">[v] Token metadata pro požadované pole statické přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="8509a-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `threadId`  
 <span data-ttu-id="8509a-108">[v] ID podprocesu, který je v rozsahu pro požadovaný statické pole.</span><span class="sxs-lookup"><span data-stu-id="8509a-108">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="8509a-109">[out] Ukazatel na adresu statické pole, které je v rámci zadaného vlákno.</span><span class="sxs-lookup"><span data-stu-id="8509a-109">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8509a-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8509a-110">Remarks</span></span>  
 <span data-ttu-id="8509a-111">`GetThreadStaticAddress` Metoda může vrátit jednu z následujících:</span><span class="sxs-lookup"><span data-stu-id="8509a-111">The `GetThreadStaticAddress` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="8509a-112">HRESULT CORPROF_E_DATAINCOMPLETE, pokud daný statické pole nebyla přiřazena adresu v zadaném kontextu.</span><span class="sxs-lookup"><span data-stu-id="8509a-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="8509a-113">Adresy objekty, které mohou být v kolekci halda paměti.</span><span class="sxs-lookup"><span data-stu-id="8509a-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="8509a-114">Tyto adresy může zneplatní po uvolňování paměti, takže po profilery kolekce paměti by neměl předpokládat jsou platné.</span><span class="sxs-lookup"><span data-stu-id="8509a-114">These addresses may become invalid after garbage collection, so after garbage collection profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="8509a-115">Před dokončením konstruktoru třídy třídy `GetThreadStaticAddress` vrátí CORPROF_E_DATAINCOMPLETE pro všechna její statické pole, i když některé statických polí mohou již být inicializován a vytvoření kořenového adresáře objekty kolekce paměti.</span><span class="sxs-lookup"><span data-stu-id="8509a-115">Before a class’s class constructor is completed, `GetThreadStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8509a-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8509a-116">Requirements</span></span>  
 <span data-ttu-id="8509a-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8509a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8509a-118">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8509a-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8509a-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8509a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8509a-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8509a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8509a-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="8509a-121">See Also</span></span>  
 [<span data-ttu-id="8509a-122">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8509a-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="8509a-123">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8509a-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
