---
title: ICorProfilerInfo::GetEventMask – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetEventMask
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetEventMask
helpviewer_keywords:
- GetEventMask method [.NET Framework profiling]
- ICorProfilerInfo::GetEventMask method [.NET Framework profiling]
ms.assetid: ec34cc13-45a3-4695-abc3-b3347d4e6fc2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 27f346679055534c3f48d0f55f0589b9c3872e2a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762792"
---
# <a name="icorprofilerinfogeteventmask-method"></a><span data-ttu-id="3bb40-102">ICorProfilerInfo::GetEventMask – metoda</span><span class="sxs-lookup"><span data-stu-id="3bb40-102">ICorProfilerInfo::GetEventMask Method</span></span>
<span data-ttu-id="3bb40-103">Získá aktuální kategorie událostí, pro které profileru chce obdržet oznámení událostí z common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="3bb40-103">Gets the current event categories for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bb40-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3bb40-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventMask(  
    [out] DWORD *pdwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3bb40-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3bb40-105">Parameters</span></span>  
 `pdwEvents`  
 <span data-ttu-id="3bb40-106">[out] Ukazatel na 4bajtovou hodnotu, která určuje kategorie událostí.</span><span class="sxs-lookup"><span data-stu-id="3bb40-106">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="3bb40-107">Každý bit určuje různé možnosti, chování nebo typ události.</span><span class="sxs-lookup"><span data-stu-id="3bb40-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="3bb40-108">Bity jsou popsány v [cor_prf_monitor –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="3bb40-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3bb40-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3bb40-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3bb40-110">Měli byste zavolat [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) metoda namísto této metody.</span><span class="sxs-lookup"><span data-stu-id="3bb40-110">You should call the [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="3bb40-111">I když `SetEventMask` metody jsou nadále podporované, [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) poskytuje další funkce.</span><span class="sxs-lookup"><span data-stu-id="3bb40-111">Although the `SetEventMask` method continues to be supported, [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bb40-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3bb40-112">Requirements</span></span>  
 <span data-ttu-id="3bb40-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bb40-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bb40-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3bb40-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3bb40-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3bb40-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3bb40-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bb40-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bb40-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3bb40-117">See also</span></span>

- [<span data-ttu-id="3bb40-118">GetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="3bb40-118">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
- [<span data-ttu-id="3bb40-119">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3bb40-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
