---
title: ICorProfilerInfo3::GetThreadStaticAddress2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetThreadStaticAddress2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2
helpviewer_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2 method [.NET Framework profiling]
- GetThreadStaticAddress2 method [.NET Framework profiling]
ms.assetid: a9608861-ae64-4467-8a73-be05ad34beac
topic_type:
- apiref
ms.openlocfilehash: a27e7ca156ca138078215a65486ac4b965c6a93d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496331"
---
# <a name="icorprofilerinfo3getthreadstaticaddress2-method"></a><span data-ttu-id="afae2-102">ICorProfilerInfo3::GetThreadStaticAddress2 – metoda</span><span class="sxs-lookup"><span data-stu-id="afae2-102">ICorProfilerInfo3::GetThreadStaticAddress2 Method</span></span>
<span data-ttu-id="afae2-103">Získá adresu zadaného pole statického vlákna, které je v oboru zadaného vlákna a domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="afae2-103">Gets the address of the specified thread-static field that is in the scope of the specified thread and application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afae2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="afae2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStaticAddress2(  
                [in] ClassID classId,  
                [in] mdFieldDef fieldToken,  
                [in] AppDomainID appDomainId,  
                [in] ThreadID threadId,  
                [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="afae2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="afae2-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="afae2-106">pro ID třídy, která obsahuje požadované pole se statickým vláknem.</span><span class="sxs-lookup"><span data-stu-id="afae2-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="afae2-107">pro Token metadat pro požadované pole se statickým vláknem</span><span class="sxs-lookup"><span data-stu-id="afae2-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="afae2-108">pro ID domény aplikace</span><span class="sxs-lookup"><span data-stu-id="afae2-108">[in] The ID of the application domain.</span></span>  
  
 `threadId`  
 <span data-ttu-id="afae2-109">pro ID vlákna, které je oborem požadovaného statického pole.</span><span class="sxs-lookup"><span data-stu-id="afae2-109">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="afae2-110">mimo Ukazatel na adresu statického pole, které je v zadaném vlákně.</span><span class="sxs-lookup"><span data-stu-id="afae2-110">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="afae2-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="afae2-111">Remarks</span></span>  
 <span data-ttu-id="afae2-112">`GetThreadStaticAddress2`Metoda může vracet jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="afae2-112">The `GetThreadStaticAddress2` method may return one of the following:</span></span>  
  
- <span data-ttu-id="afae2-113">CORPROF_E_DATAINCOMPLETE HRESULT, pokud danému statickému poli nebyla přiřazena adresa v zadaném kontextu.</span><span class="sxs-lookup"><span data-stu-id="afae2-113">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="afae2-114">Adresy objektů, které mohou být v haldě uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="afae2-114">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="afae2-115">Tyto adresy se můžou po uvolnění paměti stát neplatnými, takže po uvolnění paměti by profilery neměly předpokládat, že jsou platné.</span><span class="sxs-lookup"><span data-stu-id="afae2-115">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="afae2-116">Před dokončením konstruktoru třídy třídy `GetThreadStaticAddress2` vrátí CORPROF_E_DATAINCOMPLETE pro všechna jeho statická pole, i když některá z statických polí již mohou být inicializována a kořenové objekty uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="afae2-116">Before a class’s class constructor is completed, `GetThreadStaticAddress2` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
 <span data-ttu-id="afae2-117">Metoda [ICorProfilerInfo2:: GetThreadStaticAddress –](icorprofilerinfo2-getthreadstaticaddress-method.md) je podobná `GetThreadStaticAddress2` metodě, ale nepřijímá argument domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="afae2-117">The [ICorProfilerInfo2::GetThreadStaticAddress](icorprofilerinfo2-getthreadstaticaddress-method.md) method is similar to the `GetThreadStaticAddress2` method, but does not accept an application domain argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afae2-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="afae2-118">Requirements</span></span>  
 <span data-ttu-id="afae2-119">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afae2-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afae2-120">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="afae2-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="afae2-121">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="afae2-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="afae2-122">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afae2-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afae2-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="afae2-123">See also</span></span>

- [<span data-ttu-id="afae2-124">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="afae2-124">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="afae2-125">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="afae2-125">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="afae2-126">Profilace</span><span class="sxs-lookup"><span data-stu-id="afae2-126">Profiling</span></span>](index.md)
