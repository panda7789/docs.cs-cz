---
title: ICorProfilerInfo::SetEventMask – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetEventMask
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetEventMask
helpviewer_keywords:
- ICorProfilerInfo::SetEventMask method [.NET Framework profiling]
- SetEventMask method [.NET Framework profiling]
ms.assetid: 44bc0f56-32fa-491e-a62d-52fc96d48125
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 66a59fd338b9cbaadb2c19d0957c38ffe1af25e9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471287"
---
# <a name="icorprofilerinfoseteventmask-method"></a><span data-ttu-id="95c76-102">ICorProfilerInfo::SetEventMask – metoda</span><span class="sxs-lookup"><span data-stu-id="95c76-102">ICorProfilerInfo::SetEventMask Method</span></span>
<span data-ttu-id="95c76-103">Nastaví hodnotu, která určuje typy událostí, pro které profileru chce obdržet oznámení z common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="95c76-103">Sets a value that specifies the types of events for which the profiler wants to receive notification from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95c76-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95c76-104">Syntax</span></span>  
  
```  
HRESULT SetEventMask(  
    [in] DWORD dwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95c76-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="95c76-105">Parameters</span></span>  
 `dwEvents`  
 <span data-ttu-id="95c76-106">[in] 4 bajty. hodnota, která určuje kategorie událostí.</span><span class="sxs-lookup"><span data-stu-id="95c76-106">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="95c76-107">Každý bit určuje různé možnosti, chování nebo typ události.</span><span class="sxs-lookup"><span data-stu-id="95c76-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="95c76-108">Bity jsou popsány v [cor_prf_monitor –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="95c76-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95c76-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="95c76-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="95c76-110">Měli byste zavolat [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metoda namísto této metody.</span><span class="sxs-lookup"><span data-stu-id="95c76-110">You should call the [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="95c76-111">I když `SetEventMask` metody jsou nadále podporované, [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) poskytuje další funkce.</span><span class="sxs-lookup"><span data-stu-id="95c76-111">Although the `SetEventMask` method continues to be supported, [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95c76-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="95c76-112">Requirements</span></span>  
 <span data-ttu-id="95c76-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95c76-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95c76-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="95c76-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="95c76-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95c76-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95c76-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95c76-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95c76-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="95c76-117">See also</span></span>
- [<span data-ttu-id="95c76-118">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="95c76-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="95c76-119">SetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="95c76-119">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
