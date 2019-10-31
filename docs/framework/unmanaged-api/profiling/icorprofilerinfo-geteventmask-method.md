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
ms.openlocfilehash: f6a4ee32d1f0bd6f66b2cd2249dd90522062cdab
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120953"
---
# <a name="icorprofilerinfogeteventmask-method"></a><span data-ttu-id="f3908-102">ICorProfilerInfo::GetEventMask – metoda</span><span class="sxs-lookup"><span data-stu-id="f3908-102">ICorProfilerInfo::GetEventMask Method</span></span>
<span data-ttu-id="f3908-103">Získá aktuální kategorie událostí, pro které profiler chce přijímat oznámení o událostech z modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="f3908-103">Gets the current event categories for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3908-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3908-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventMask(  
    [out] DWORD *pdwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3908-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f3908-105">Parameters</span></span>  
 `pdwEvents`  
 <span data-ttu-id="f3908-106">mimo Ukazatel na hodnotu 4 bajty, která určuje kategorie událostí.</span><span class="sxs-lookup"><span data-stu-id="f3908-106">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="f3908-107">Každý bit ovládá jinou schopnost, chování nebo typ události.</span><span class="sxs-lookup"><span data-stu-id="f3908-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="f3908-108">Bity jsou popsány ve výčtu [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="f3908-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3908-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f3908-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f3908-110">Místo této metody byste měli zavolat metodu [GetEventMask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f3908-110">You should call the [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="f3908-111">I když je nadále podporována metoda `SetEventMask`, [GetEventMask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) poskytuje další funkce.</span><span class="sxs-lookup"><span data-stu-id="f3908-111">Although the `SetEventMask` method continues to be supported, [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3908-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f3908-112">Requirements</span></span>  
 <span data-ttu-id="f3908-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3908-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3908-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f3908-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f3908-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f3908-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3908-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3908-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3908-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f3908-117">See also</span></span>

- [<span data-ttu-id="f3908-118">GetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="f3908-118">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
- [<span data-ttu-id="f3908-119">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f3908-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
