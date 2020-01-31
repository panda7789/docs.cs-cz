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
ms.openlocfilehash: ed39411fa88c38da58e8a881c47d19b3b8c9ff8d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76869275"
---
# <a name="icorprofilerinfoseteventmask-method"></a><span data-ttu-id="18a2b-102">ICorProfilerInfo::SetEventMask – metoda</span><span class="sxs-lookup"><span data-stu-id="18a2b-102">ICorProfilerInfo::SetEventMask Method</span></span>
<span data-ttu-id="18a2b-103">Nastaví hodnotu, která určuje typy událostí, pro které profiler chce dostávat oznámení z modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="18a2b-103">Sets a value that specifies the types of events for which the profiler wants to receive notification from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18a2b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18a2b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEventMask(  
    [in] DWORD dwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18a2b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="18a2b-105">Parameters</span></span>  
 `dwEvents`  
 <span data-ttu-id="18a2b-106">pro Hodnota 4 bajtu, která určuje kategorie událostí.</span><span class="sxs-lookup"><span data-stu-id="18a2b-106">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="18a2b-107">Každý bit ovládá jinou schopnost, chování nebo typ události.</span><span class="sxs-lookup"><span data-stu-id="18a2b-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="18a2b-108">Bity jsou popsány v [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="18a2b-108">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18a2b-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="18a2b-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="18a2b-110">Místo této metody byste měli zavolat metodu [SetEventMask2 –](icorprofilerinfo5-seteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="18a2b-110">You should call the [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="18a2b-111">I když je nadále podporována metoda `SetEventMask`, [SetEventMask2 –](icorprofilerinfo5-seteventmask2-method.md) poskytuje další funkce.</span><span class="sxs-lookup"><span data-stu-id="18a2b-111">Although the `SetEventMask` method continues to be supported, [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18a2b-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="18a2b-112">Requirements</span></span>  
 <span data-ttu-id="18a2b-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18a2b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18a2b-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="18a2b-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="18a2b-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="18a2b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18a2b-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18a2b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18a2b-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="18a2b-117">See also</span></span>

- [<span data-ttu-id="18a2b-118">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18a2b-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="18a2b-119">SetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="18a2b-119">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)
