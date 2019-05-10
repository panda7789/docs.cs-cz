---
title: ICorProfilerInfo2::GetRVAStaticAddress – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetRVAStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetRVAStaticAddress
helpviewer_keywords:
- GetRVAStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetRVAStaticAddress method [.NET Framework profiling]
ms.assetid: a25a8f8b-5cfa-440d-9376-a1a1c3a9fc11
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8c2d1aee741ac54e861f7068d883731745ca7788
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64584309"
---
# <a name="icorprofilerinfo2getrvastaticaddress-method"></a><span data-ttu-id="e06bb-102">ICorProfilerInfo2::GetRVAStaticAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="e06bb-102">ICorProfilerInfo2::GetRVAStaticAddress Method</span></span>
<span data-ttu-id="e06bb-103">Získá adresu statické pole zadanou relativní virtuální adresu (RVA).</span><span class="sxs-lookup"><span data-stu-id="e06bb-103">Gets the address of the specified relative virtual address (RVA) static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e06bb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e06bb-104">Syntax</span></span>  
  
```  
HRESULT GetRVAStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e06bb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e06bb-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="e06bb-106">[in] ID třídy, která obsahuje požadovaná pole statickou adresu RVA.</span><span class="sxs-lookup"><span data-stu-id="e06bb-106">[in] The ID of the class that contains the requested RVA-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="e06bb-107">[in] Token metadat pro požadované pole statickou adresu RVA.</span><span class="sxs-lookup"><span data-stu-id="e06bb-107">[in] Metadata token for the requested RVA-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="e06bb-108">[out] Ukazatel na adresu RVA statické pole.</span><span class="sxs-lookup"><span data-stu-id="e06bb-108">[out] A pointer to the address of the RVA-static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e06bb-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e06bb-109">Remarks</span></span>  
 <span data-ttu-id="e06bb-110">`GetRVAStaticAddress` Metoda může vrátit jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="e06bb-110">The `GetRVAStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="e06bb-111">CORPROF_E_DATAINCOMPLETE HRESULT, pokud daný statické pole nebyla přiřazena adresa v zadaném kontextu.</span><span class="sxs-lookup"><span data-stu-id="e06bb-111">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="e06bb-112">Adresy objektů, které mohou být v haldě uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="e06bb-112">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="e06bb-113">Tyto adresy mohou stát neplatnými po uvolnění paměti, takže po uvolnění paměti, profilovací programy by neměl se předpokládá, že jsou platné.</span><span class="sxs-lookup"><span data-stu-id="e06bb-113">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="e06bb-114">Před dokončením konstruktoru třídy třídy `GetRVAStaticAddress` vrátí CORPROF_E_DATAINCOMPLETE pro všechny jeho statická pole, i když některé z statická pole může být již inicializován a může být kořenová objekty uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="e06bb-114">Before a class’s class constructor is completed, `GetRVAStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and may be rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e06bb-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e06bb-115">Requirements</span></span>  
 <span data-ttu-id="e06bb-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e06bb-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e06bb-117">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e06bb-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e06bb-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e06bb-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e06bb-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e06bb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e06bb-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e06bb-120">See also</span></span>

- [<span data-ttu-id="e06bb-121">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e06bb-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="e06bb-122">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e06bb-122">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
