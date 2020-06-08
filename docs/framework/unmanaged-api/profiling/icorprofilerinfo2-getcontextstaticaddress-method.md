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
ms.openlocfilehash: 7550caaa7cb4d7ed77dc36ecf0ce0e0cbc541db7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497059"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a><span data-ttu-id="caeae-102">ICorProfilerInfo2::GetContextStaticAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="caeae-102">ICorProfilerInfo2::GetContextStaticAddress Method</span></span>
<span data-ttu-id="caeae-103">Získá adresu pro zadané kontextové a statické pole, které je v rozsahu zadaného kontextu.</span><span class="sxs-lookup"><span data-stu-id="caeae-103">Gets the address for the specified context-static field that is in the scope of the specified context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caeae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="caeae-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="caeae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="caeae-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="caeae-106">pro ID třídy, která obsahuje požadovaný kontext a statické pole.</span><span class="sxs-lookup"><span data-stu-id="caeae-106">[in] The ID of the class that contains the requested context-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="caeae-107">pro Token metadat pro požadované kontextové a statické pole.</span><span class="sxs-lookup"><span data-stu-id="caeae-107">[in] The metadata token for the requested context-static field.</span></span>  
  
 `contextId`  
 <span data-ttu-id="caeae-108">pro ID kontextu, který je oborem pro požadovaný kontext a statické pole.</span><span class="sxs-lookup"><span data-stu-id="caeae-108">[in] The ID of the context that is the scope for the requested context-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="caeae-109">mimo Ukazatel na adresu statického pole, které je v zadaném kontextu.</span><span class="sxs-lookup"><span data-stu-id="caeae-109">[out] A pointer to the address of the static field that is within the specified context.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="caeae-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="caeae-110">Remarks</span></span>  
 <span data-ttu-id="caeae-111">`GetContextStaticAddress`Metoda může vracet jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="caeae-111">The `GetContextStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="caeae-112">CORPROF_E_DATAINCOMPLETE HRESULT, pokud danému statickému poli nebyla přiřazena adresa v zadaném kontextu.</span><span class="sxs-lookup"><span data-stu-id="caeae-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="caeae-113">Adresy objektů, které mohou být v haldě uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="caeae-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="caeae-114">Tyto adresy se můžou po uvolnění paměti stát neplatnými, takže po uvolnění paměti by profilery neměly předpokládat, že jsou platné.</span><span class="sxs-lookup"><span data-stu-id="caeae-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="caeae-115">Před dokončením konstruktoru třídy třídy `GetContextStaticAddress` vrátí CORPROF_E_DATAINCOMPLETE pro všechna jeho statická pole, i když některá z statických polí již mohou být inicializována a kořenové objekty uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="caeae-115">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="caeae-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="caeae-116">Requirements</span></span>  
 <span data-ttu-id="caeae-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="caeae-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="caeae-118">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="caeae-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="caeae-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="caeae-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="caeae-120">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="caeae-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caeae-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="caeae-121">See also</span></span>

- [<span data-ttu-id="caeae-122">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="caeae-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="caeae-123">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="caeae-123">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
