---
title: ICorProfilerInfo5::SetEventMask2 – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- IcorProfilerInfo5.SetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 05dbbe2b-049c-4a60-be69-2ad7a949405e
topic_type:
- apiref
ms.openlocfilehash: 8027cdcde8281c363207e309bf65fcd90c03b626
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495616"
---
# <a name="icorprofilerinfo5seteventmask2-method"></a><span data-ttu-id="015f3-102">ICorProfilerInfo5::SetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="015f3-102">ICorProfilerInfo5::SetEventMask2 Method</span></span>
<span data-ttu-id="015f3-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="015f3-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="015f3-104">Nastaví hodnotu, která určuje typy událostí, pro které profiler chce přijímat oznámení o událostech z modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="015f3-104">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span> <span data-ttu-id="015f3-105">Poskytuje více funkcí než metoda [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="015f3-105">It provides more functionality than the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="015f3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="015f3-106">Syntax</span></span>  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="015f3-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="015f3-107">Parameters</span></span>  
 `dwEventsLow`  
 <span data-ttu-id="015f3-108">pro Hodnota 4 bajtu, která určuje kategorie událostí.</span><span class="sxs-lookup"><span data-stu-id="015f3-108">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="015f3-109">Každý bit ovládá jinou schopnost, chování nebo typ události.</span><span class="sxs-lookup"><span data-stu-id="015f3-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="015f3-110">Bity jsou popsány v [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="015f3-110">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `dwEventsHigh`  
 <span data-ttu-id="015f3-111">pro Hodnota 4 bajtu, která určuje kategorie událostí.</span><span class="sxs-lookup"><span data-stu-id="015f3-111">[in] A 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="015f3-112">Každý bit ovládá jinou schopnost, chování nebo typ události.</span><span class="sxs-lookup"><span data-stu-id="015f3-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="015f3-113">Bity jsou popsány v [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="015f3-113">The bits are described in the [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="015f3-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="015f3-114">Remarks</span></span>  
 <span data-ttu-id="015f3-115">`SetEventMask2`Metoda slouží k nastavení zpětných volání, ke kterým se Profiler přihlašuje.</span><span class="sxs-lookup"><span data-stu-id="015f3-115">The `SetEventMask2` method is used to set the callbacks to which the profiler subscribes.</span></span> <span data-ttu-id="015f3-116">Obvykle zavoláte metodu [GetEventMask2 –](icorprofilerinfo5-geteventmask2-method.md) k určení, které bity jsou nastaveny, proveďte logické nebo její hodnoty a `pdwEventsLow` `pdwEventsHigh` všechny nové bity, které chcete nastavit, a poté zavolejte `SetEventMask2` metodu.</span><span class="sxs-lookup"><span data-stu-id="015f3-116">Typically, you call the [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) method to determine which bits are set, perform a logical OR of its `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the `SetEventMask2` method.</span></span>  
  
 <span data-ttu-id="015f3-117">Tato metoda je doporučená alternativou k metodě [SetEventMask](icorprofilerinfo-seteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="015f3-117">This method is the recommended alternative to the [SetEventMask](icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="015f3-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="015f3-118">Requirements</span></span>  
 <span data-ttu-id="015f3-119">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="015f3-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="015f3-120">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="015f3-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="015f3-121">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="015f3-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="015f3-122">**Verze .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="015f3-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="015f3-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="015f3-123">See also</span></span>

- [<span data-ttu-id="015f3-124">ICorProfilerInfo5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="015f3-124">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)
- [<span data-ttu-id="015f3-125">Metoda GetEventMask2</span><span class="sxs-lookup"><span data-stu-id="015f3-125">GetEventMask2 Method</span></span>](icorprofilerinfo5-geteventmask2-method.md)
