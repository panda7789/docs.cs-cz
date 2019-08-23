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
ms.openlocfilehash: e11628f9c20160899f37e62472547eaa98ea60b8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962655"
---
# <a name="icorprofilerinfoseteventmask-method"></a><span data-ttu-id="b7d8d-102">ICorProfilerInfo::SetEventMask – metoda</span><span class="sxs-lookup"><span data-stu-id="b7d8d-102">ICorProfilerInfo::SetEventMask Method</span></span>
<span data-ttu-id="b7d8d-103">Nastaví hodnotu, která určuje typy událostí, pro které profiler chce dostávat oznámení z modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="b7d8d-103">Sets a value that specifies the types of events for which the profiler wants to receive notification from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7d8d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7d8d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEventMask(  
    [in] DWORD dwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7d8d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b7d8d-105">Parameters</span></span>  
 `dwEvents`  
 <span data-ttu-id="b7d8d-106">pro Hodnota 4 bajtu, která určuje kategorie událostí.</span><span class="sxs-lookup"><span data-stu-id="b7d8d-106">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="b7d8d-107">Každý bit ovládá jinou schopnost, chování nebo typ události.</span><span class="sxs-lookup"><span data-stu-id="b7d8d-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="b7d8d-108">Bity jsou popsány ve výčtu [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="b7d8d-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7d8d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b7d8d-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b7d8d-110">Místo této metody byste měli zavolat metodu [SetEventMask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b7d8d-110">You should call the [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="b7d8d-111">I když `SetEventMask` je metoda stále podporovaná, [SetEventMask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) poskytuje další funkce.</span><span class="sxs-lookup"><span data-stu-id="b7d8d-111">Although the `SetEventMask` method continues to be supported, [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7d8d-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b7d8d-112">Requirements</span></span>  
 <span data-ttu-id="b7d8d-113">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7d8d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7d8d-114">**Hlaviček** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b7d8d-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b7d8d-115">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7d8d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7d8d-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7d8d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7d8d-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b7d8d-117">See also</span></span>

- [<span data-ttu-id="b7d8d-118">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7d8d-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="b7d8d-119">SetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="b7d8d-119">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
