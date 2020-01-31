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
ms.openlocfilehash: d99e5000cdd0d7252764554025815dbace2289f4
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868678"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a><span data-ttu-id="e03f6-102">ICorProfilerInfo2::GetContextStaticAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="e03f6-102">ICorProfilerInfo2::GetContextStaticAddress Method</span></span>
<span data-ttu-id="e03f6-103">Získá adresu pro zadané kontextové a statické pole, které je v rozsahu zadaného kontextu.</span><span class="sxs-lookup"><span data-stu-id="e03f6-103">Gets the address for the specified context-static field that is in the scope of the specified context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e03f6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e03f6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e03f6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e03f6-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="e03f6-106">pro ID třídy, která obsahuje požadovaný kontext a statické pole.</span><span class="sxs-lookup"><span data-stu-id="e03f6-106">[in] The ID of the class that contains the requested context-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="e03f6-107">pro Token metadat pro požadované kontextové a statické pole.</span><span class="sxs-lookup"><span data-stu-id="e03f6-107">[in] The metadata token for the requested context-static field.</span></span>  
  
 `contextId`  
 <span data-ttu-id="e03f6-108">pro ID kontextu, který je oborem pro požadovaný kontext a statické pole.</span><span class="sxs-lookup"><span data-stu-id="e03f6-108">[in] The ID of the context that is the scope for the requested context-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="e03f6-109">mimo Ukazatel na adresu statického pole, které je v zadaném kontextu.</span><span class="sxs-lookup"><span data-stu-id="e03f6-109">[out] A pointer to the address of the static field that is within the specified context.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e03f6-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e03f6-110">Remarks</span></span>  
 <span data-ttu-id="e03f6-111">Metoda `GetContextStaticAddress` může vracet jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="e03f6-111">The `GetContextStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="e03f6-112">CORPROF_E_DATAINCOMPLETE HRESULT, pokud danému statickému poli nebyla přiřazena adresa v zadaném kontextu.</span><span class="sxs-lookup"><span data-stu-id="e03f6-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="e03f6-113">Adresy objektů, které mohou být v haldě uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="e03f6-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="e03f6-114">Tyto adresy se můžou po uvolnění paměti stát neplatnými, takže po uvolnění paměti by profilery neměly předpokládat, že jsou platné.</span><span class="sxs-lookup"><span data-stu-id="e03f6-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="e03f6-115">Před dokončením konstruktoru třídy třídy `GetContextStaticAddress` vrátí CORPROF_E_DATAINCOMPLETE pro všechna jeho statická pole, i když některá z statických polí již mohou být inicializována a kořenové objekty uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="e03f6-115">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e03f6-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e03f6-116">Requirements</span></span>  
 <span data-ttu-id="e03f6-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e03f6-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e03f6-118">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e03f6-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e03f6-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e03f6-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e03f6-120">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e03f6-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e03f6-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e03f6-121">See also</span></span>

- [<span data-ttu-id="e03f6-122">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e03f6-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="e03f6-123">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e03f6-123">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
