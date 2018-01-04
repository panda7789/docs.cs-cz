---
title: "ICorProfilerInfo2::GetAppDomainStaticAddress – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetAppDomainStaticAddress
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetAppDomainStaticAddress
helpviewer_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress method [.NET Framework profiling]
- GetAppDomainStaticAddress method [.NET Framework profiling]
ms.assetid: 2a9e0ea7-a9e2-4817-b1c4-fcf15b215ea9
topic_type: apiref
caps.latest.revision: "22"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2fad6cccc3992f001780bf8bd1a4c879dc6aa754
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a><span data-ttu-id="c9ae4-102">ICorProfilerInfo2::GetAppDomainStaticAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="c9ae4-102">ICorProfilerInfo2::GetAppDomainStaticAddress Method</span></span>
<span data-ttu-id="c9ae4-103">Získá adresu domény statické pole určená aplikace, které je v oboru domény zadané aplikace.</span><span class="sxs-lookup"><span data-stu-id="c9ae4-103">Gets the address of the specified application domain-static field that is in the scope of the specified application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9ae4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9ae4-104">Syntax</span></span>  
  
```  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9ae4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c9ae4-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="c9ae4-106">[v] ID třídy třídy, která obsahuje pole domény statické požadovaná aplikace.</span><span class="sxs-lookup"><span data-stu-id="c9ae4-106">[in] The class ID of the class that contains the requested application domain-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="c9ae4-107">[v] Token metadata pro domény statické pole požadovaná aplikace.</span><span class="sxs-lookup"><span data-stu-id="c9ae4-107">[in] The metadata token for the requested application domain-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="c9ae4-108">[v] ID domény aplikace, které je v rozsahu pro požadovaný statické pole.</span><span class="sxs-lookup"><span data-stu-id="c9ae4-108">[in] The ID of the application domain that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="c9ae4-109">[out] Ukazatel na adresu statického pole, která je v rámci domény zadané aplikace.</span><span class="sxs-lookup"><span data-stu-id="c9ae4-109">[out] A pointer to the address of the static field that is within the specified application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9ae4-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c9ae4-110">Remarks</span></span>  
 <span data-ttu-id="c9ae4-111">`GetAppDomainStaticAddress` Metoda může vrátit jednu z následujících:</span><span class="sxs-lookup"><span data-stu-id="c9ae4-111">The `GetAppDomainStaticAddress` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="c9ae4-112">HRESULT CORPROF_E_DATAINCOMPLETE, pokud daný statické pole nebyla přiřazena adresu v zadaném kontextu.</span><span class="sxs-lookup"><span data-stu-id="c9ae4-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="c9ae4-113">Adresy objekty, které mohou být v kolekci halda paměti.</span><span class="sxs-lookup"><span data-stu-id="c9ae4-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="c9ae4-114">Tyto adresy může zneplatní po uvolňování paměti, takže po uvolnění paměti by neměl profilery předpokládá platnými.</span><span class="sxs-lookup"><span data-stu-id="c9ae4-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="c9ae4-115">Před dokončením konstruktoru třídy třídy `GetAppDomainStaticAddress` vrátí CORPROF_E_DATAINCOMPLETE pro všechna její statické pole, i když některé statických polí mohou již být inicializován a vytvoření kořenového adresáře objekty kolekce paměti.</span><span class="sxs-lookup"><span data-stu-id="c9ae4-115">Before a class’s class constructor is completed, `GetAppDomainStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9ae4-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c9ae4-116">Requirements</span></span>  
 <span data-ttu-id="c9ae4-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9ae4-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9ae4-118">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c9ae4-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c9ae4-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9ae4-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9ae4-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9ae4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9ae4-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="c9ae4-121">See Also</span></span>  
 [<span data-ttu-id="c9ae4-122">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c9ae4-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="c9ae4-123">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c9ae4-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
