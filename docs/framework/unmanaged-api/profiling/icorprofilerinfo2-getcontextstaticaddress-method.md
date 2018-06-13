---
title: ICorProfilerInfo2::GetContextStaticAddress – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetContextStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetContextStaticAddress
helpviewer_keywords:
- GetContextStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetContextStaticAddress method [.NET Framework profiling]
ms.assetid: 2b374116-0972-416a-8cf5-79213129be9a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d787e3eae59218c46a95c327a0f93502c3833d9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33456232"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a><span data-ttu-id="721bc-102">ICorProfilerInfo2::GetContextStaticAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="721bc-102">ICorProfilerInfo2::GetContextStaticAddress Method</span></span>
<span data-ttu-id="721bc-103">Získá adresu pro zadaný kontext statické pole, která je v rozsahu zadaný kontext.</span><span class="sxs-lookup"><span data-stu-id="721bc-103">Gets the address for the specified context-static field that is in the scope of the specified context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="721bc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="721bc-104">Syntax</span></span>  
  
```  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="721bc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="721bc-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="721bc-106">[v] ID třídy, která obsahuje požadovanou kontextu statické pole.</span><span class="sxs-lookup"><span data-stu-id="721bc-106">[in] The ID of the class that contains the requested context-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="721bc-107">[v] Token metadata pro požadované pole kontextu statické.</span><span class="sxs-lookup"><span data-stu-id="721bc-107">[in] The metadata token for the requested context-static field.</span></span>  
  
 `contextId`  
 <span data-ttu-id="721bc-108">[v] ID kontext, který je v rozsahu pro požadované pole kontextu statické.</span><span class="sxs-lookup"><span data-stu-id="721bc-108">[in] The ID of the context that is the scope for the requested context-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="721bc-109">[out] Ukazatel na adresu statické pole, která je v rámci zadaného kontextu.</span><span class="sxs-lookup"><span data-stu-id="721bc-109">[out] A pointer to the address of the static field that is within the specified context.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="721bc-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="721bc-110">Remarks</span></span>  
 <span data-ttu-id="721bc-111">`GetContextStaticAddress` Metoda může vrátit jednu z následujících:</span><span class="sxs-lookup"><span data-stu-id="721bc-111">The `GetContextStaticAddress` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="721bc-112">HRESULT CORPROF_E_DATAINCOMPLETE, pokud daný statické pole nebyla přiřazena adresu v zadaném kontextu.</span><span class="sxs-lookup"><span data-stu-id="721bc-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="721bc-113">Adresy objekty, které mohou být v kolekci halda paměti.</span><span class="sxs-lookup"><span data-stu-id="721bc-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="721bc-114">Tyto adresy může zneplatní po uvolňování paměti, takže po uvolnění paměti by neměl profilery předpokládá platnými.</span><span class="sxs-lookup"><span data-stu-id="721bc-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="721bc-115">Před dokončením konstruktoru třídy třídy `GetContextStaticAddress` vrátí CORPROF_E_DATAINCOMPLETE pro všechna její statické pole, i když některé statických polí mohou již být inicializován a vytvoření kořenového adresáře objekty kolekce paměti.</span><span class="sxs-lookup"><span data-stu-id="721bc-115">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="721bc-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="721bc-116">Requirements</span></span>  
 <span data-ttu-id="721bc-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="721bc-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="721bc-118">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="721bc-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="721bc-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="721bc-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="721bc-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="721bc-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="721bc-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="721bc-121">See Also</span></span>  
 [<span data-ttu-id="721bc-122">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="721bc-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="721bc-123">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="721bc-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
