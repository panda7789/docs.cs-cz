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
ms.openlocfilehash: 63f19fe899abd75380249e171f248480949bc471
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863904"
---
# <a name="icorprofilerinfogeteventmask-method"></a><span data-ttu-id="42289-102">ICorProfilerInfo::GetEventMask – metoda</span><span class="sxs-lookup"><span data-stu-id="42289-102">ICorProfilerInfo::GetEventMask Method</span></span>
<span data-ttu-id="42289-103">Získá aktuální kategorie událostí, pro které profiler chce přijímat oznámení o událostech z modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="42289-103">Gets the current event categories for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42289-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42289-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventMask(  
    [out] DWORD *pdwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42289-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="42289-105">Parameters</span></span>  
 `pdwEvents`  
 <span data-ttu-id="42289-106">mimo Ukazatel na hodnotu 4 bajty, která určuje kategorie událostí.</span><span class="sxs-lookup"><span data-stu-id="42289-106">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="42289-107">Každý bit ovládá jinou schopnost, chování nebo typ události.</span><span class="sxs-lookup"><span data-stu-id="42289-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="42289-108">Bity jsou popsány v [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="42289-108">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42289-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="42289-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="42289-110">Místo této metody byste měli zavolat metodu [GetEventMask2 –](icorprofilerinfo5-geteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="42289-110">You should call the [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="42289-111">I když je nadále podporována metoda `SetEventMask`, [GetEventMask2 –](icorprofilerinfo5-geteventmask2-method.md) poskytuje další funkce.</span><span class="sxs-lookup"><span data-stu-id="42289-111">Although the `SetEventMask` method continues to be supported, [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42289-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="42289-112">Requirements</span></span>  
 <span data-ttu-id="42289-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42289-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42289-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="42289-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="42289-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="42289-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42289-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42289-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42289-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="42289-117">See also</span></span>

- [<span data-ttu-id="42289-118">GetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="42289-118">GetEventMask2 Method</span></span>](icorprofilerinfo5-geteventmask2-method.md)
- [<span data-ttu-id="42289-119">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="42289-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
