---
title: "ICorProfilerInfo::GetEventMask – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetEventMask
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetEventMask
helpviewer_keywords:
- GetEventMask method [.NET Framework profiling]
- ICorProfilerInfo::GetEventMask method [.NET Framework profiling]
ms.assetid: ec34cc13-45a3-4695-abc3-b3347d4e6fc2
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8757298819f5ca6a534a12cec0593aed05610042
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfogeteventmask-method"></a><span data-ttu-id="68e10-102">ICorProfilerInfo::GetEventMask – metoda</span><span class="sxs-lookup"><span data-stu-id="68e10-102">ICorProfilerInfo::GetEventMask Method</span></span>
<span data-ttu-id="68e10-103">Získá aktuální kategorií událostí, pro které profileru chce dostávat oznámení o událostech, modul CLR (CLR).</span><span class="sxs-lookup"><span data-stu-id="68e10-103">Gets the current event categories for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68e10-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68e10-104">Syntax</span></span>  
  
```  
HRESULT GetEventMask(  
    [out] DWORD *pdwEvents);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="68e10-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="68e10-105">Parameters</span></span>  
 `pdwEvents`  
 <span data-ttu-id="68e10-106">[out] Ukazatel na hodnotu 4 bajtů, která určuje kategorie události.</span><span class="sxs-lookup"><span data-stu-id="68e10-106">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="68e10-107">Každý bit řídí jinou možnost, chování nebo typ události.</span><span class="sxs-lookup"><span data-stu-id="68e10-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="68e10-108">Službu bits, jsou popsané v [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="68e10-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68e10-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="68e10-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68e10-110">Měli byste zavolat [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) metoda namísto této metody.</span><span class="sxs-lookup"><span data-stu-id="68e10-110">You should call the [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="68e10-111">I když `SetEventMask` metoda nadále podporován, [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) poskytuje další funkce.</span><span class="sxs-lookup"><span data-stu-id="68e10-111">Although the `SetEventMask` method continues to be supported, [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68e10-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="68e10-112">Requirements</span></span>  
 <span data-ttu-id="68e10-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68e10-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68e10-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="68e10-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="68e10-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68e10-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68e10-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68e10-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68e10-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="68e10-117">See Also</span></span>  
 [<span data-ttu-id="68e10-118">Metoda GetEventMask2</span><span class="sxs-lookup"><span data-stu-id="68e10-118">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)  
 [<span data-ttu-id="68e10-119">Icorprofilerinfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="68e10-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
