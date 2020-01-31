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
ms.openlocfilehash: ca64d4f5932fb4a0c0486fee5ca1017a6d3adaf2
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868626"
---
# <a name="icorprofilerinfo2getrvastaticaddress-method"></a><span data-ttu-id="c6488-102">ICorProfilerInfo2::GetRVAStaticAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="c6488-102">ICorProfilerInfo2::GetRVAStaticAddress Method</span></span>
<span data-ttu-id="c6488-103">Získá adresu zadaného statického pole virtuální adresy (RVA).</span><span class="sxs-lookup"><span data-stu-id="c6488-103">Gets the address of the specified relative virtual address (RVA) static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6488-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6488-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRVAStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6488-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c6488-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="c6488-106">pro ID třídy, která obsahuje požadované pole RVA-static.</span><span class="sxs-lookup"><span data-stu-id="c6488-106">[in] The ID of the class that contains the requested RVA-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="c6488-107">pro Token metadat pro požadované pole RVA – static</span><span class="sxs-lookup"><span data-stu-id="c6488-107">[in] Metadata token for the requested RVA-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="c6488-108">mimo Ukazatel na adresu pole RVA-static.</span><span class="sxs-lookup"><span data-stu-id="c6488-108">[out] A pointer to the address of the RVA-static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6488-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c6488-109">Remarks</span></span>  
 <span data-ttu-id="c6488-110">Metoda `GetRVAStaticAddress` může vracet jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="c6488-110">The `GetRVAStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="c6488-111">CORPROF_E_DATAINCOMPLETE HRESULT, pokud danému statickému poli nebyla přiřazena adresa v zadaném kontextu.</span><span class="sxs-lookup"><span data-stu-id="c6488-111">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="c6488-112">Adresy objektů, které mohou být v haldě uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="c6488-112">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="c6488-113">Tyto adresy se můžou po uvolnění paměti stát neplatnými, takže po uvolnění paměti by profilery neměly předpokládat, že jsou platné.</span><span class="sxs-lookup"><span data-stu-id="c6488-113">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="c6488-114">Před dokončením konstruktoru třídy třídy `GetRVAStaticAddress` vrátí CORPROF_E_DATAINCOMPLETE pro všechna jeho statická pole, i když některá z statických polí již mohou být inicializována a mohou být kořenem objektů uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="c6488-114">Before a class’s class constructor is completed, `GetRVAStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and may be rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6488-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c6488-115">Requirements</span></span>  
 <span data-ttu-id="c6488-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6488-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6488-117">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c6488-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c6488-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c6488-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6488-119">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6488-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6488-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6488-120">See also</span></span>

- [<span data-ttu-id="c6488-121">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c6488-121">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="c6488-122">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c6488-122">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
