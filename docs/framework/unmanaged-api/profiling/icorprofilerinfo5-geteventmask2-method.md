---
title: ICorProfilerInfo5::GetEventMask2 – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerInfo5.GetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: f854b68f-009c-4ffb-89cd-ca874d1c0fb7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 467be5a02b2e202b2e0e4f6a36b748ab6e0e8dbc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54731215"
---
# <a name="icorprofilerinfo5geteventmask2-method"></a><span data-ttu-id="12f42-102">ICorProfilerInfo5::GetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="12f42-102">ICorProfilerInfo5::GetEventMask2 Method</span></span>
<span data-ttu-id="12f42-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="12f42-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="12f42-104">Získá aktuální kategorie událostí, pro které profileru chce, aby dostávala oznámení z common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="12f42-104">Gets the current event categories for which the profiler wants to receive notifications from the common language runtime (CLR).</span></span>  <span data-ttu-id="12f42-105">Poskytuje funkce není poskytovaný [icorprofilerinfo::geteventmask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="12f42-105">It provides functionality not provided by the [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12f42-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12f42-106">Syntax</span></span>  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="12f42-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="12f42-107">Parameters</span></span>  
 `pdwEventsLow`  
 <span data-ttu-id="12f42-108">[out] Ukazatel na 4bajtovou hodnotu, která určuje kategorie událostí.</span><span class="sxs-lookup"><span data-stu-id="12f42-108">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="12f42-109">Každý bit určuje různé možnosti, chování nebo typ události.</span><span class="sxs-lookup"><span data-stu-id="12f42-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="12f42-110">Bity jsou popsány v [cor_prf_monitor –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="12f42-110">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `pdwEventsHigh`  
 <span data-ttu-id="12f42-111">[out] Ukazatel na 4bajtovou hodnotu, která určuje kategorie událostí.</span><span class="sxs-lookup"><span data-stu-id="12f42-111">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="12f42-112">Každý bit určuje různé možnosti, chování nebo typ události.</span><span class="sxs-lookup"><span data-stu-id="12f42-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="12f42-113">Bity jsou popsány v [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="12f42-113">The bits are described in the [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12f42-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="12f42-114">Remarks</span></span>  
 <span data-ttu-id="12f42-115">`GetEventMask2` Metoda se používá k určení které zpětná volání profileru přihlásí k odběru.</span><span class="sxs-lookup"><span data-stu-id="12f42-115">The `GetEventMask2` method is used to determine which callbacks the profiler has subscribed to.</span></span> <span data-ttu-id="12f42-116">Obvykle provádíte logický OR `pdwEventsLow` a `pdwEventsHigh` hodnoty a všechny nové bity, které chcete nastavit a následně zavolat [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="12f42-116">Typically, you perform a logical OR of the `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
 <span data-ttu-id="12f42-117">Tato metoda je doporučenou alternativou k [geteventmask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="12f42-117">This method is the recommended alternative to the [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12f42-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="12f42-118">Requirements</span></span>  
 <span data-ttu-id="12f42-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12f42-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12f42-120">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="12f42-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="12f42-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12f42-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12f42-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12f42-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12f42-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12f42-123">See also</span></span>
- [<span data-ttu-id="12f42-124">ICorProfilerInfo5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="12f42-124">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
- [<span data-ttu-id="12f42-125">SetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="12f42-125">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
