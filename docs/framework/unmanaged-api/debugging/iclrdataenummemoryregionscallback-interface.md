---
title: ICLRDataEnumMemoryRegionsCallback – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegionsCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegionsCallback
helpviewer_keywords:
- ICLRDataEnumMemoryRegionsCallback interface [.NET Framework debugging]
ms.assetid: 3f1af8b0-8478-48e0-a7ec-3e90e0b97649
topic_type:
- apiref
ms.openlocfilehash: cf46133095d1345ffbe0356d3ab486c11ae6dbd6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122916"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="9caf9-102">ICLRDataEnumMemoryRegionsCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9caf9-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>
<span data-ttu-id="9caf9-103">Poskytuje metodu zpětného volání pro [ICLRDataEnumMemoryRegions –:: EnumMemoryRegions –](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) , která oznamuje ladicímu programu výsledek pokusu o vytvoření výčtu konkrétní oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="9caf9-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9caf9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9caf9-104">Methods</span></span>  
  
|<span data-ttu-id="9caf9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9caf9-105">Method</span></span>|<span data-ttu-id="9caf9-106">Popis</span><span class="sxs-lookup"><span data-stu-id="9caf9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9caf9-107">EnumMemoryRegion – metoda</span><span class="sxs-lookup"><span data-stu-id="9caf9-107">EnumMemoryRegion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="9caf9-108">Volá se `ICLRDataEnumMemoryRegions::EnumMemoryRegions`, aby se nahlásila ladicímu programu v důsledku pokusu o vytvoření výčtu konkrétní oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="9caf9-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9caf9-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9caf9-109">Requirements</span></span>  
 <span data-ttu-id="9caf9-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9caf9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9caf9-111">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="9caf9-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="9caf9-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9caf9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9caf9-113">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9caf9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9caf9-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9caf9-114">See also</span></span>

- [<span data-ttu-id="9caf9-115">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="9caf9-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
