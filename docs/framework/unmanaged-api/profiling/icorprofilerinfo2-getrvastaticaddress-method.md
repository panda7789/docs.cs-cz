---
title: "ICorProfilerInfo2::GetRVAStaticAddress – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetRVAStaticAddress
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetRVAStaticAddress
helpviewer_keywords:
- GetRVAStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetRVAStaticAddress method [.NET Framework profiling]
ms.assetid: a25a8f8b-5cfa-440d-9376-a1a1c3a9fc11
topic_type: apiref
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4320ed3cdd3d17932d03e98d4d35d27adad2532a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getrvastaticaddress-method"></a><span data-ttu-id="c1728-102">ICorProfilerInfo2::GetRVAStaticAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="c1728-102">ICorProfilerInfo2::GetRVAStaticAddress Method</span></span>
<span data-ttu-id="c1728-103">Získá adresu statická pole relativní zadané virtuální adresy (RVA).</span><span class="sxs-lookup"><span data-stu-id="c1728-103">Gets the address of the specified relative virtual address (RVA) static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1728-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1728-104">Syntax</span></span>  
  
```  
HRESULT GetRVAStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c1728-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c1728-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="c1728-106">[v] ID třídy, která obsahuje požadovanou RVA statické pole.</span><span class="sxs-lookup"><span data-stu-id="c1728-106">[in] The ID of the class that contains the requested RVA-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="c1728-107">[v] Metadata token pro požadované pole RVA statické.</span><span class="sxs-lookup"><span data-stu-id="c1728-107">[in] Metadata token for the requested RVA-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="c1728-108">[out] Ukazatel na adresu RVA statické pole.</span><span class="sxs-lookup"><span data-stu-id="c1728-108">[out] A pointer to the address of the RVA-static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1728-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c1728-109">Remarks</span></span>  
 <span data-ttu-id="c1728-110">`GetRVAStaticAddress` Metoda může vrátit jednu z následujících:</span><span class="sxs-lookup"><span data-stu-id="c1728-110">The `GetRVAStaticAddress` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="c1728-111">HRESULT CORPROF_E_DATAINCOMPLETE, pokud daný statické pole nebyla přiřazena adresu v zadaném kontextu.</span><span class="sxs-lookup"><span data-stu-id="c1728-111">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="c1728-112">Adresy objekty, které mohou být v kolekci halda paměti.</span><span class="sxs-lookup"><span data-stu-id="c1728-112">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="c1728-113">Tyto adresy může zneplatní po uvolňování paměti, takže po uvolnění paměti by neměl profilery předpokládá platnými.</span><span class="sxs-lookup"><span data-stu-id="c1728-113">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="c1728-114">Před dokončením konstruktoru třídy třídy `GetRVAStaticAddress` vrátí CORPROF_E_DATAINCOMPLETE pro všechna její statické pole, i když některé statických polí může již inicializován a může být vytvoření kořenového adresáře objekty kolekce paměti.</span><span class="sxs-lookup"><span data-stu-id="c1728-114">Before a class’s class constructor is completed, `GetRVAStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and may be rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1728-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c1728-115">Requirements</span></span>  
 <span data-ttu-id="c1728-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1728-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1728-117">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c1728-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c1728-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1728-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1728-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1728-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1728-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="c1728-120">See Also</span></span>  
 [<span data-ttu-id="c1728-121">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c1728-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="c1728-122">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c1728-122">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
