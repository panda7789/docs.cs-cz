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
ms.openlocfilehash: 05d8c44655d8670194035c336bd62ae5d53bfec3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862968"
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a><span data-ttu-id="9f110-102">ICorProfilerInfo2::GetAppDomainStaticAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="9f110-102">ICorProfilerInfo2::GetAppDomainStaticAddress Method</span></span>
<span data-ttu-id="9f110-103">Získá adresu zadaného pole domény aplikace (static), které je v oboru zadané domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="9f110-103">Gets the address of the specified application domain-static field that is in the scope of the specified application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f110-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f110-104">Syntax</span></span>  
  
```cpp  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f110-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9f110-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="9f110-106">pro ID třídy, která obsahuje požadované pole aplikační doména (static).</span><span class="sxs-lookup"><span data-stu-id="9f110-106">[in] The class ID of the class that contains the requested application domain-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="9f110-107">pro Token metadat pro požadované pole aplikační domény – static</span><span class="sxs-lookup"><span data-stu-id="9f110-107">[in] The metadata token for the requested application domain-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="9f110-108">pro ID domény aplikace, která je oborem požadovaného statického pole.</span><span class="sxs-lookup"><span data-stu-id="9f110-108">[in] The ID of the application domain that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="9f110-109">mimo Ukazatel na adresu statického pole, které je v zadané doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="9f110-109">[out] A pointer to the address of the static field that is within the specified application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f110-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9f110-110">Remarks</span></span>  
 <span data-ttu-id="9f110-111">Metoda `GetAppDomainStaticAddress` může vracet jednu z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="9f110-111">The `GetAppDomainStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="9f110-112">CORPROF_E_DATAINCOMPLETE HRESULT, pokud danému statickému poli nebyla přiřazena adresa v zadaném kontextu.</span><span class="sxs-lookup"><span data-stu-id="9f110-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="9f110-113">Adresy objektů, které mohou být v haldě uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="9f110-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="9f110-114">Tyto adresy se můžou po uvolnění paměti stát neplatnými, takže po uvolnění paměti by profilery neměly předpokládat, že jsou platné.</span><span class="sxs-lookup"><span data-stu-id="9f110-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="9f110-115">Před dokončením konstruktoru třídy třídy `GetAppDomainStaticAddress` vrátí CORPROF_E_DATAINCOMPLETE pro všechna jeho statická pole, i když některá z statických polí již mohou být inicializována a kořenové objekty uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="9f110-115">Before a class’s class constructor is completed, `GetAppDomainStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f110-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9f110-116">Requirements</span></span>  
 <span data-ttu-id="9f110-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f110-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f110-118">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9f110-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9f110-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9f110-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f110-120">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f110-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f110-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f110-121">See also</span></span>

- [<span data-ttu-id="9f110-122">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9f110-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="9f110-123">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9f110-123">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
