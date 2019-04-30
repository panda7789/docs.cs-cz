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
ms.openlocfilehash: e8a842dd531576b1029c3924d12b1a4bd95bde37
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791557"
---
# <a name="icorprofilerinfo2getthreadstaticaddress-method"></a><span data-ttu-id="1e57c-102">ICorProfilerInfo2::GetThreadStaticAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="1e57c-102">ICorProfilerInfo2::GetThreadStaticAddress Method</span></span>
<span data-ttu-id="1e57c-103">Získá adresu zadané pole vlákna, která je v rámci zadaného vlákna.</span><span class="sxs-lookup"><span data-stu-id="1e57c-103">Gets the address of the specified thread-static field that is in the scope of the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e57c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e57c-104">Syntax</span></span>  
  
```  
HRESULT GetThreadStaticAddress(  
    [in] ClassID     classId,  
    [in] mdFieldDef  fieldToken,  
    [in] ThreadID    threadId,  
    [out] void       **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e57c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1e57c-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="1e57c-106">[in] ID třídy, která obsahuje požadovaná pole statická na úrovni vlákna.</span><span class="sxs-lookup"><span data-stu-id="1e57c-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="1e57c-107">[in] Token metadat pro požadované pole statická na úrovni vlákna.</span><span class="sxs-lookup"><span data-stu-id="1e57c-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `threadId`  
 <span data-ttu-id="1e57c-108">[in] ID vlákna, která je v oboru pro požadovaný statické pole.</span><span class="sxs-lookup"><span data-stu-id="1e57c-108">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="1e57c-109">[out] Ukazatel na adresu statické pole, která je v rámci zadaného vlákna.</span><span class="sxs-lookup"><span data-stu-id="1e57c-109">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e57c-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1e57c-110">Remarks</span></span>  
 <span data-ttu-id="1e57c-111">`GetThreadStaticAddress` Metoda může vrátit jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="1e57c-111">The `GetThreadStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="1e57c-112">CORPROF_E_DATAINCOMPLETE HRESULT, pokud daný statické pole nebyla přiřazena adresa v zadaném kontextu.</span><span class="sxs-lookup"><span data-stu-id="1e57c-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="1e57c-113">Adresy objektů, které mohou být v haldě uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="1e57c-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="1e57c-114">Tyto adresy můžou stát neplatnými po uvolnění paměti, takže se po uvolňování paměti kolekce profilovací programy by neměl předpokládají, že jsou platné.</span><span class="sxs-lookup"><span data-stu-id="1e57c-114">These addresses may become invalid after garbage collection, so after garbage collection profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="1e57c-115">Před dokončením konstruktoru třídy třídy `GetThreadStaticAddress` vrátí CORPROF_E_DATAINCOMPLETE pro všechny jeho statická pole, i když některé statická pole může již být inicializován a kořenová objekty uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="1e57c-115">Before a class’s class constructor is completed, `GetThreadStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e57c-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1e57c-116">Requirements</span></span>  
 <span data-ttu-id="1e57c-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e57c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e57c-118">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1e57c-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1e57c-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1e57c-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e57c-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e57c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e57c-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1e57c-121">See also</span></span>

- [<span data-ttu-id="1e57c-122">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1e57c-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="1e57c-123">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1e57c-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
