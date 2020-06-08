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
ms.openlocfilehash: 3dc5f04504cca632892c16d31c92a33935b356e0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497332"
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a><span data-ttu-id="04d24-102">ICorProfilerInfo2::GetAppDomainStaticAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="04d24-102">ICorProfilerInfo2::GetAppDomainStaticAddress Method</span></span>
<span data-ttu-id="04d24-103">Získá adresu zadaného pole domény aplikace (static), které je v oboru zadané domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="04d24-103">Gets the address of the specified application domain-static field that is in the scope of the specified application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04d24-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04d24-104">Syntax</span></span>  
  
```cpp  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04d24-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="04d24-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="04d24-106">pro ID třídy, která obsahuje požadované pole aplikační doména (static).</span><span class="sxs-lookup"><span data-stu-id="04d24-106">[in] The class ID of the class that contains the requested application domain-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="04d24-107">pro Token metadat pro požadované pole aplikační domény – static</span><span class="sxs-lookup"><span data-stu-id="04d24-107">[in] The metadata token for the requested application domain-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="04d24-108">pro ID domény aplikace, která je oborem požadovaného statického pole.</span><span class="sxs-lookup"><span data-stu-id="04d24-108">[in] The ID of the application domain that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="04d24-109">mimo Ukazatel na adresu statického pole, které je v zadané doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="04d24-109">[out] A pointer to the address of the static field that is within the specified application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04d24-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="04d24-110">Remarks</span></span>  
 <span data-ttu-id="04d24-111">`GetAppDomainStaticAddress`Metoda může vracet jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="04d24-111">The `GetAppDomainStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="04d24-112">CORPROF_E_DATAINCOMPLETE HRESULT, pokud danému statickému poli nebyla přiřazena adresa v zadaném kontextu.</span><span class="sxs-lookup"><span data-stu-id="04d24-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="04d24-113">Adresy objektů, které mohou být v haldě uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="04d24-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="04d24-114">Tyto adresy se můžou po uvolnění paměti stát neplatnými, takže po uvolnění paměti by profilery neměly předpokládat, že jsou platné.</span><span class="sxs-lookup"><span data-stu-id="04d24-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="04d24-115">Před dokončením konstruktoru třídy třídy `GetAppDomainStaticAddress` vrátí CORPROF_E_DATAINCOMPLETE pro všechna jeho statická pole, i když některá z statických polí již mohou být inicializována a kořenové objekty uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="04d24-115">Before a class’s class constructor is completed, `GetAppDomainStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04d24-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="04d24-116">Requirements</span></span>  
 <span data-ttu-id="04d24-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04d24-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04d24-118">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="04d24-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="04d24-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="04d24-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04d24-120">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04d24-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04d24-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04d24-121">See also</span></span>

- [<span data-ttu-id="04d24-122">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="04d24-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="04d24-123">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="04d24-123">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
