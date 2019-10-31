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
ms.openlocfilehash: b79668130570dc69a580fbf7da4dc122389d9ef0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136701"
---
# <a name="icorprofilerinfoseteventmask-method"></a><span data-ttu-id="c677e-102">ICorProfilerInfo::SetEventMask – metoda</span><span class="sxs-lookup"><span data-stu-id="c677e-102">ICorProfilerInfo::SetEventMask Method</span></span>
<span data-ttu-id="c677e-103">Nastaví hodnotu, která určuje typy událostí, pro které profiler chce dostávat oznámení z modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="c677e-103">Sets a value that specifies the types of events for which the profiler wants to receive notification from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c677e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c677e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEventMask(  
    [in] DWORD dwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c677e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c677e-105">Parameters</span></span>  
 `dwEvents`  
 <span data-ttu-id="c677e-106">pro Hodnota 4 bajtu, která určuje kategorie událostí.</span><span class="sxs-lookup"><span data-stu-id="c677e-106">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="c677e-107">Každý bit ovládá jinou schopnost, chování nebo typ události.</span><span class="sxs-lookup"><span data-stu-id="c677e-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="c677e-108">Bity jsou popsány ve výčtu [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="c677e-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c677e-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c677e-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c677e-110">Místo této metody byste měli zavolat metodu [SetEventMask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c677e-110">You should call the [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="c677e-111">I když je nadále podporována metoda `SetEventMask`, [SetEventMask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) poskytuje další funkce.</span><span class="sxs-lookup"><span data-stu-id="c677e-111">Although the `SetEventMask` method continues to be supported, [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c677e-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c677e-112">Requirements</span></span>  
 <span data-ttu-id="c677e-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c677e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c677e-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c677e-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c677e-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c677e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c677e-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c677e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c677e-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c677e-117">See also</span></span>

- [<span data-ttu-id="c677e-118">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c677e-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="c677e-119">SetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="c677e-119">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
