---
title: ICorProfilerInfo2::GetAppDomainStaticAddress – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetAppDomainStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress
helpviewer_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress method [.NET Framework profiling]
- GetAppDomainStaticAddress method [.NET Framework profiling]
ms.assetid: 2a9e0ea7-a9e2-4817-b1c4-fcf15b215ea9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2095f02cb23c3580b0a1109e8f0da669f61adabc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789386"
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a><span data-ttu-id="5ef88-102">ICorProfilerInfo2::GetAppDomainStaticAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="5ef88-102">ICorProfilerInfo2::GetAppDomainStaticAddress Method</span></span>
<span data-ttu-id="5ef88-103">Získá adresu zadané aplikace domény statická pole, které je v oboru zadanou doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="5ef88-103">Gets the address of the specified application domain-static field that is in the scope of the specified application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ef88-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ef88-104">Syntax</span></span>  
  
```  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ef88-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5ef88-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="5ef88-106">[in] ID třídy třídy, která obsahuje doménu statické pole požadovaná aplikace.</span><span class="sxs-lookup"><span data-stu-id="5ef88-106">[in] The class ID of the class that contains the requested application domain-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="5ef88-107">[in] Token metadat pro domény statické pole požadované aplikace.</span><span class="sxs-lookup"><span data-stu-id="5ef88-107">[in] The metadata token for the requested application domain-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="5ef88-108">[in] ID domény aplikace, která je v oboru pro požadovaný statické pole.</span><span class="sxs-lookup"><span data-stu-id="5ef88-108">[in] The ID of the application domain that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="5ef88-109">[out] Ukazatel na adresu statické pole, která je určená aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="5ef88-109">[out] A pointer to the address of the static field that is within the specified application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ef88-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5ef88-110">Remarks</span></span>  
 <span data-ttu-id="5ef88-111">`GetAppDomainStaticAddress` Metoda může vrátit jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="5ef88-111">The `GetAppDomainStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="5ef88-112">CORPROF_E_DATAINCOMPLETE HRESULT, pokud daný statické pole nebyla přiřazena adresa v zadaném kontextu.</span><span class="sxs-lookup"><span data-stu-id="5ef88-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="5ef88-113">Adresy objektů, které mohou být v haldě uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="5ef88-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="5ef88-114">Tyto adresy mohou stát neplatnými po uvolnění paměti, takže po uvolnění paměti, profilovací programy by neměl se předpokládá, že jsou platné.</span><span class="sxs-lookup"><span data-stu-id="5ef88-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="5ef88-115">Před dokončením konstruktoru třídy třídy `GetAppDomainStaticAddress` vrátí CORPROF_E_DATAINCOMPLETE pro všechny jeho statická pole, i když některé statická pole může již být inicializován a kořenová objekty uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="5ef88-115">Before a class’s class constructor is completed, `GetAppDomainStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ef88-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5ef88-116">Requirements</span></span>  
 <span data-ttu-id="5ef88-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ef88-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ef88-118">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5ef88-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5ef88-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ef88-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ef88-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ef88-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ef88-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5ef88-121">See also</span></span>

- [<span data-ttu-id="5ef88-122">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5ef88-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="5ef88-123">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5ef88-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
