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
ms.openlocfilehash: c68668c1d591a8fb53d04d632027b0d8effb0c42
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474797"
---
# <a name="icorprofilerinfo5geteventmask2-method"></a><span data-ttu-id="a799c-102">ICorProfilerInfo5::GetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="a799c-102">ICorProfilerInfo5::GetEventMask2 Method</span></span>
<span data-ttu-id="a799c-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="a799c-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="a799c-104">Získá aktuální kategorie událostí, pro které profileru chce, aby dostávala oznámení z common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="a799c-104">Gets the current event categories for which the profiler wants to receive notifications from the common language runtime (CLR).</span></span>  <span data-ttu-id="a799c-105">Poskytuje funkce není poskytovaný [icorprofilerinfo::geteventmask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="a799c-105">It provides functionality not provided by the [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a799c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a799c-106">Syntax</span></span>  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a799c-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="a799c-107">Parameters</span></span>  
 `pdwEventsLow`  
 <span data-ttu-id="a799c-108">[out] Ukazatel na 4bajtovou hodnotu, která určuje kategorie událostí.</span><span class="sxs-lookup"><span data-stu-id="a799c-108">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="a799c-109">Každý bit určuje různé možnosti, chování nebo typ události.</span><span class="sxs-lookup"><span data-stu-id="a799c-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="a799c-110">Bity jsou popsány v [cor_prf_monitor –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="a799c-110">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `pdwEventsHigh`  
 <span data-ttu-id="a799c-111">[out] Ukazatel na 4bajtovou hodnotu, která určuje kategorie událostí.</span><span class="sxs-lookup"><span data-stu-id="a799c-111">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="a799c-112">Každý bit určuje různé možnosti, chování nebo typ události.</span><span class="sxs-lookup"><span data-stu-id="a799c-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="a799c-113">Bity jsou popsány v [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="a799c-113">The bits are described in the [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a799c-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a799c-114">Remarks</span></span>  
 <span data-ttu-id="a799c-115">`GetEventMask2` Metoda se používá k určení které zpětná volání profileru přihlásí k odběru.</span><span class="sxs-lookup"><span data-stu-id="a799c-115">The `GetEventMask2` method is used to determine which callbacks the profiler has subscribed to.</span></span> <span data-ttu-id="a799c-116">Obvykle provádíte logický OR `pdwEventsLow` a `pdwEventsHigh` hodnoty a všechny nové bity, které chcete nastavit a následně zavolat [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="a799c-116">Typically, you perform a logical OR of the `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
 <span data-ttu-id="a799c-117">Tato metoda je doporučenou alternativou k [geteventmask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="a799c-117">This method is the recommended alternative to the [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a799c-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a799c-118">Requirements</span></span>  
 <span data-ttu-id="a799c-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a799c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a799c-120">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a799c-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a799c-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a799c-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a799c-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a799c-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a799c-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a799c-123">See also</span></span>
- [<span data-ttu-id="a799c-124">ICorProfilerInfo5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a799c-124">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
- [<span data-ttu-id="a799c-125">SetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="a799c-125">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
