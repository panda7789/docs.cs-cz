---
title: ICorProfilerInfo5::GetEventMask2 – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerInfo5.GetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: f854b68f-009c-4ffb-89cd-ca874d1c0fb7
topic_type:
- apiref
ms.openlocfilehash: f3943eef969f777b40dc51c4900b190561f14887
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868392"
---
# <a name="icorprofilerinfo5geteventmask2-method"></a><span data-ttu-id="86f02-102">ICorProfilerInfo5::GetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="86f02-102">ICorProfilerInfo5::GetEventMask2 Method</span></span>
<span data-ttu-id="86f02-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="86f02-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="86f02-104">Získá aktuální kategorie událostí, pro které profiler chce dostávat oznámení z modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="86f02-104">Gets the current event categories for which the profiler wants to receive notifications from the common language runtime (CLR).</span></span>  <span data-ttu-id="86f02-105">Poskytuje funkce, které nejsou poskytovány metodou [ICorProfilerInfo:: GetEventMask –](icorprofilerinfo-geteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="86f02-105">It provides functionality not provided by the [ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86f02-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86f02-106">Syntax</span></span>  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86f02-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="86f02-107">Parameters</span></span>  
 `pdwEventsLow`  
 <span data-ttu-id="86f02-108">mimo Ukazatel na hodnotu 4 bajty, která určuje kategorie událostí.</span><span class="sxs-lookup"><span data-stu-id="86f02-108">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="86f02-109">Každý bit ovládá jinou schopnost, chování nebo typ události.</span><span class="sxs-lookup"><span data-stu-id="86f02-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="86f02-110">Bity jsou popsány v [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="86f02-110">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `pdwEventsHigh`  
 <span data-ttu-id="86f02-111">mimo Ukazatel na hodnotu 4 bajty, která určuje kategorie událostí.</span><span class="sxs-lookup"><span data-stu-id="86f02-111">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="86f02-112">Každý bit ovládá jinou schopnost, chování nebo typ události.</span><span class="sxs-lookup"><span data-stu-id="86f02-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="86f02-113">Bity jsou popsány v [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="86f02-113">The bits are described in the [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86f02-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="86f02-114">Remarks</span></span>  
 <span data-ttu-id="86f02-115">Metoda `GetEventMask2` slouží k určení, která zpětná volání profileru se přihlásí k odběru.</span><span class="sxs-lookup"><span data-stu-id="86f02-115">The `GetEventMask2` method is used to determine which callbacks the profiler has subscribed to.</span></span> <span data-ttu-id="86f02-116">Obvykle provedete logickou hodnotu nebo `pdwEventsLow` a `pdwEventsHigh` hodnoty a jakékoli nové bity, které chcete nastavit, a potom zavoláte metodu [SetEventMask2 –](icorprofilerinfo5-seteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="86f02-116">Typically, you perform a logical OR of the `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
 <span data-ttu-id="86f02-117">Tato metoda je doporučená alternativou k metodě [GetEventMask –](icorprofilerinfo-geteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="86f02-117">This method is the recommended alternative to the [GetEventMask](icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86f02-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="86f02-118">Requirements</span></span>  
 <span data-ttu-id="86f02-119">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86f02-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86f02-120">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="86f02-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="86f02-121">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="86f02-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86f02-122">**Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86f02-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86f02-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="86f02-123">See also</span></span>

- [<span data-ttu-id="86f02-124">ICorProfilerInfo5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="86f02-124">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)
- [<span data-ttu-id="86f02-125">SetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="86f02-125">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)
