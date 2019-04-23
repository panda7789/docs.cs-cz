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
ms.openlocfilehash: 46fd79931e7f2f05b1b17ebca3f8cff28c152ff4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59221424"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a><span data-ttu-id="7ace1-102">ICorProfilerInfo2::GetContextStaticAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="7ace1-102">ICorProfilerInfo2::GetContextStaticAddress Method</span></span>
<span data-ttu-id="7ace1-103">Získá adresu pro zadaný kontext statická pole, která je v rámci zadaného kontextu.</span><span class="sxs-lookup"><span data-stu-id="7ace1-103">Gets the address for the specified context-static field that is in the scope of the specified context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ace1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ace1-104">Syntax</span></span>  
  
```  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ace1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7ace1-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="7ace1-106">[in] ID třídy, která obsahuje požadovaná pole statického kontextu.</span><span class="sxs-lookup"><span data-stu-id="7ace1-106">[in] The ID of the class that contains the requested context-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="7ace1-107">[in] Token metadat pro požadované pole statického kontextu.</span><span class="sxs-lookup"><span data-stu-id="7ace1-107">[in] The metadata token for the requested context-static field.</span></span>  
  
 `contextId`  
 <span data-ttu-id="7ace1-108">[in] ID kontextu, který je rozsah pro požadované pole statického kontextu.</span><span class="sxs-lookup"><span data-stu-id="7ace1-108">[in] The ID of the context that is the scope for the requested context-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="7ace1-109">[out] Ukazatel na adresu statické pole, která je v rámci zadaného kontextu.</span><span class="sxs-lookup"><span data-stu-id="7ace1-109">[out] A pointer to the address of the static field that is within the specified context.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ace1-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7ace1-110">Remarks</span></span>  
 <span data-ttu-id="7ace1-111">`GetContextStaticAddress` Metoda může vrátit jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="7ace1-111">The `GetContextStaticAddress` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="7ace1-112">CORPROF_E_DATAINCOMPLETE HRESULT, pokud daný statické pole nebyla přiřazena adresa v zadaném kontextu.</span><span class="sxs-lookup"><span data-stu-id="7ace1-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="7ace1-113">Adresy objektů, které mohou být v haldě uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="7ace1-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="7ace1-114">Tyto adresy mohou stát neplatnými po uvolnění paměti, takže po uvolnění paměti, profilovací programy by neměl se předpokládá, že jsou platné.</span><span class="sxs-lookup"><span data-stu-id="7ace1-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="7ace1-115">Před dokončením konstruktoru třídy třídy `GetContextStaticAddress` vrátí CORPROF_E_DATAINCOMPLETE pro všechny jeho statická pole, i když některé statická pole může již být inicializován a kořenová objekty uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="7ace1-115">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ace1-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7ace1-116">Requirements</span></span>  
 <span data-ttu-id="7ace1-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ace1-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ace1-118">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7ace1-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7ace1-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ace1-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ace1-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ace1-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ace1-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7ace1-121">See also</span></span>

- [<span data-ttu-id="7ace1-122">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7ace1-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="7ace1-123">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7ace1-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
