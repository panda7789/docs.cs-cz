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
ms.openlocfilehash: 3df6e4decf1c4641116dee5fab3ca83189b427c0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496760"
---
# <a name="icorprofilerinfo2getthreadstaticaddress-method"></a><span data-ttu-id="25665-102">ICorProfilerInfo2::GetThreadStaticAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="25665-102">ICorProfilerInfo2::GetThreadStaticAddress Method</span></span>
<span data-ttu-id="25665-103">Získá adresu zadaného pole statického vlákna, které je v rozsahu zadaného vlákna.</span><span class="sxs-lookup"><span data-stu-id="25665-103">Gets the address of the specified thread-static field that is in the scope of the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25665-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25665-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStaticAddress(  
    [in] ClassID     classId,  
    [in] mdFieldDef  fieldToken,  
    [in] ThreadID    threadId,  
    [out] void       **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25665-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="25665-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="25665-106">pro ID třídy, která obsahuje požadované pole se statickým vláknem.</span><span class="sxs-lookup"><span data-stu-id="25665-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="25665-107">pro Token metadat pro požadované pole se statickým vláknem</span><span class="sxs-lookup"><span data-stu-id="25665-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `threadId`  
 <span data-ttu-id="25665-108">pro ID vlákna, které je oborem požadovaného statického pole.</span><span class="sxs-lookup"><span data-stu-id="25665-108">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="25665-109">mimo Ukazatel na adresu statického pole, které je v zadaném vlákně.</span><span class="sxs-lookup"><span data-stu-id="25665-109">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25665-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="25665-110">Remarks</span></span>  
 <span data-ttu-id="25665-111">`GetThreadStaticAddress`Metoda může vracet jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="25665-111">The `GetThreadStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="25665-112">CORPROF_E_DATAINCOMPLETE HRESULT, pokud danému statickému poli nebyla přiřazena adresa v zadaném kontextu.</span><span class="sxs-lookup"><span data-stu-id="25665-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="25665-113">Adresy objektů, které mohou být v haldě uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="25665-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="25665-114">Tyto adresy se můžou po uvolnění paměti stát neplatnými, takže po profilech pro uvolňování paměti by nemělo předpokládat, že jsou platné.</span><span class="sxs-lookup"><span data-stu-id="25665-114">These addresses may become invalid after garbage collection, so after garbage collection profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="25665-115">Před dokončením konstruktoru třídy třídy `GetThreadStaticAddress` vrátí CORPROF_E_DATAINCOMPLETE pro všechna jeho statická pole, i když některá z statických polí již mohou být inicializována a kořenové objekty uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="25665-115">Before a class’s class constructor is completed, `GetThreadStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25665-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="25665-116">Requirements</span></span>  
 <span data-ttu-id="25665-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25665-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25665-118">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="25665-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="25665-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="25665-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25665-120">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25665-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25665-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="25665-121">See also</span></span>

- [<span data-ttu-id="25665-122">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="25665-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="25665-123">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="25665-123">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
