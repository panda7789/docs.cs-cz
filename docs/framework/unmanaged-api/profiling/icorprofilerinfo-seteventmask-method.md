---
title: "ICorProfilerInfo::SetEventMask – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4c6fe763103e7b8aaf6d501c653342a21bd513b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfoseteventmask-method"></a><span data-ttu-id="a37e8-102">ICorProfilerInfo::SetEventMask – metoda</span><span class="sxs-lookup"><span data-stu-id="a37e8-102">ICorProfilerInfo::SetEventMask Method</span></span>
<span data-ttu-id="a37e8-103">Nastaví hodnotu, která určuje typy událostí, pro které profileru chce dostávat oznámení, modul CLR (CLR).</span><span class="sxs-lookup"><span data-stu-id="a37e8-103">Sets a value that specifies the types of events for which the profiler wants to receive notification from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a37e8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a37e8-104">Syntax</span></span>  
  
```  
HRESULT SetEventMask(  
    [in] DWORD dwEvents);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a37e8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a37e8-105">Parameters</span></span>  
 `dwEvents`  
 <span data-ttu-id="a37e8-106">[v] 4bajtový hodnotu, která určuje kategorie události.</span><span class="sxs-lookup"><span data-stu-id="a37e8-106">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="a37e8-107">Každý bit řídí jinou možnost, chování nebo typ události.</span><span class="sxs-lookup"><span data-stu-id="a37e8-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="a37e8-108">Službu bits, jsou popsané v [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="a37e8-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a37e8-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a37e8-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a37e8-110">Měli byste zavolat [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metoda namísto této metody.</span><span class="sxs-lookup"><span data-stu-id="a37e8-110">You should call the [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="a37e8-111">I když `SetEventMask` metoda nadále podporován, [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) poskytuje další funkce.</span><span class="sxs-lookup"><span data-stu-id="a37e8-111">Although the `SetEventMask` method continues to be supported, [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a37e8-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a37e8-112">Requirements</span></span>  
 <span data-ttu-id="a37e8-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a37e8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a37e8-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a37e8-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a37e8-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a37e8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a37e8-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a37e8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a37e8-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="a37e8-117">See Also</span></span>  
 [<span data-ttu-id="a37e8-118">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a37e8-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="a37e8-119">SetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="a37e8-119">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
