---
title: "ICorProfilerInfo2::GetContextStaticAddress – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetContextStaticAddress
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetContextStaticAddress
helpviewer_keywords:
- GetContextStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetContextStaticAddress method [.NET Framework profiling]
ms.assetid: 2b374116-0972-416a-8cf5-79213129be9a
topic_type: apiref
caps.latest.revision: "23"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2d206ca90b2d89ead67f419f0f4511d19d8ce110
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a><span data-ttu-id="853e7-102">ICorProfilerInfo2::GetContextStaticAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="853e7-102">ICorProfilerInfo2::GetContextStaticAddress Method</span></span>
<span data-ttu-id="853e7-103">Získá adresu pro zadaný kontext statické pole, která je v rozsahu zadaný kontext.</span><span class="sxs-lookup"><span data-stu-id="853e7-103">Gets the address for the specified context-static field that is in the scope of the specified context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="853e7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="853e7-104">Syntax</span></span>  
  
```  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="853e7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="853e7-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="853e7-106">[v] ID třídy, která obsahuje požadovanou kontextu statické pole.</span><span class="sxs-lookup"><span data-stu-id="853e7-106">[in] The ID of the class that contains the requested context-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="853e7-107">[v] Token metadata pro požadované pole kontextu statické.</span><span class="sxs-lookup"><span data-stu-id="853e7-107">[in] The metadata token for the requested context-static field.</span></span>  
  
 `contextId`  
 <span data-ttu-id="853e7-108">[v] ID kontext, který je v rozsahu pro požadované pole kontextu statické.</span><span class="sxs-lookup"><span data-stu-id="853e7-108">[in] The ID of the context that is the scope for the requested context-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="853e7-109">[out] Ukazatel na adresu statické pole, která je v rámci zadaného kontextu.</span><span class="sxs-lookup"><span data-stu-id="853e7-109">[out] A pointer to the address of the static field that is within the specified context.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="853e7-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="853e7-110">Remarks</span></span>  
 <span data-ttu-id="853e7-111">`GetContextStaticAddress` Metoda může vrátit jednu z následujících:</span><span class="sxs-lookup"><span data-stu-id="853e7-111">The `GetContextStaticAddress` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="853e7-112">HRESULT CORPROF_E_DATAINCOMPLETE, pokud daný statické pole nebyla přiřazena adresu v zadaném kontextu.</span><span class="sxs-lookup"><span data-stu-id="853e7-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="853e7-113">Adresy objekty, které mohou být v kolekci halda paměti.</span><span class="sxs-lookup"><span data-stu-id="853e7-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="853e7-114">Tyto adresy může zneplatní po uvolňování paměti, takže po uvolnění paměti by neměl profilery předpokládá platnými.</span><span class="sxs-lookup"><span data-stu-id="853e7-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="853e7-115">Před dokončením konstruktoru třídy třídy `GetContextStaticAddress` vrátí CORPROF_E_DATAINCOMPLETE pro všechna její statické pole, i když některé statických polí mohou již být inicializován a vytvoření kořenového adresáře objekty kolekce paměti.</span><span class="sxs-lookup"><span data-stu-id="853e7-115">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="853e7-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="853e7-116">Requirements</span></span>  
 <span data-ttu-id="853e7-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="853e7-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="853e7-118">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="853e7-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="853e7-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="853e7-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="853e7-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="853e7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="853e7-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="853e7-121">See Also</span></span>  
 [<span data-ttu-id="853e7-122">Icorprofilerinfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="853e7-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="853e7-123">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="853e7-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
