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
ms.openlocfilehash: 5fea50b9d42511540197c80d4ba402834b216830
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957951"
---
# <a name="icorprofilerinfogeteventmask-method"></a><span data-ttu-id="d99ac-102">ICorProfilerInfo::GetEventMask – metoda</span><span class="sxs-lookup"><span data-stu-id="d99ac-102">ICorProfilerInfo::GetEventMask Method</span></span>
<span data-ttu-id="d99ac-103">Získá aktuální kategorie událostí, pro které profiler chce přijímat oznámení o událostech z modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="d99ac-103">Gets the current event categories for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d99ac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d99ac-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventMask(  
    [out] DWORD *pdwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d99ac-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d99ac-105">Parameters</span></span>  
 `pdwEvents`  
 <span data-ttu-id="d99ac-106">mimo Ukazatel na hodnotu 4 bajty, která určuje kategorie událostí.</span><span class="sxs-lookup"><span data-stu-id="d99ac-106">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="d99ac-107">Každý bit ovládá jinou schopnost, chování nebo typ události.</span><span class="sxs-lookup"><span data-stu-id="d99ac-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="d99ac-108">Bity jsou popsány ve výčtu [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="d99ac-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d99ac-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d99ac-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d99ac-110">Místo této metody byste měli zavolat metodu [GetEventMask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d99ac-110">You should call the [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="d99ac-111">I když `SetEventMask` je metoda stále podporovaná, [GetEventMask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) poskytuje další funkce.</span><span class="sxs-lookup"><span data-stu-id="d99ac-111">Although the `SetEventMask` method continues to be supported, [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d99ac-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d99ac-112">Requirements</span></span>  
 <span data-ttu-id="d99ac-113">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d99ac-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d99ac-114">**Hlaviček** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d99ac-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d99ac-115">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d99ac-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d99ac-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d99ac-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d99ac-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d99ac-117">See also</span></span>

- [<span data-ttu-id="d99ac-118">GetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="d99ac-118">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
- [<span data-ttu-id="d99ac-119">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d99ac-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
