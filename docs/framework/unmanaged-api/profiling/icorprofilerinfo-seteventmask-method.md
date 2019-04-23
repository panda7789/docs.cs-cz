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
ms.openlocfilehash: 122a621552b49f476f219216ac0a52011c1542ec
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59103945"
---
# <a name="icorprofilerinfoseteventmask-method"></a><span data-ttu-id="fe6f0-102">ICorProfilerInfo::SetEventMask – metoda</span><span class="sxs-lookup"><span data-stu-id="fe6f0-102">ICorProfilerInfo::SetEventMask Method</span></span>
<span data-ttu-id="fe6f0-103">Nastaví hodnotu, která určuje typy událostí, pro které profileru chce obdržet oznámení z common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="fe6f0-103">Sets a value that specifies the types of events for which the profiler wants to receive notification from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe6f0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe6f0-104">Syntax</span></span>  
  
```  
HRESULT SetEventMask(  
    [in] DWORD dwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe6f0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fe6f0-105">Parameters</span></span>  
 `dwEvents`  
 <span data-ttu-id="fe6f0-106">[in] 4 bajty. hodnota, která určuje kategorie událostí.</span><span class="sxs-lookup"><span data-stu-id="fe6f0-106">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="fe6f0-107">Každý bit určuje různé možnosti, chování nebo typ události.</span><span class="sxs-lookup"><span data-stu-id="fe6f0-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="fe6f0-108">Bity jsou popsány v [cor_prf_monitor –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="fe6f0-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe6f0-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fe6f0-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fe6f0-110">Měli byste zavolat [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metoda namísto této metody.</span><span class="sxs-lookup"><span data-stu-id="fe6f0-110">You should call the [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="fe6f0-111">I když `SetEventMask` metody jsou nadále podporované, [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) poskytuje další funkce.</span><span class="sxs-lookup"><span data-stu-id="fe6f0-111">Although the `SetEventMask` method continues to be supported, [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe6f0-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fe6f0-112">Requirements</span></span>  
 <span data-ttu-id="fe6f0-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe6f0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe6f0-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fe6f0-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fe6f0-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe6f0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe6f0-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe6f0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe6f0-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fe6f0-117">See also</span></span>

- [<span data-ttu-id="fe6f0-118">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fe6f0-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="fe6f0-119">SetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="fe6f0-119">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
