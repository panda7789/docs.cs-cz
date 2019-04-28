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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dad66c8a55982762ede754a4b3cd747b7a91b87d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698184"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="d3f67-102">ICLRDataEnumMemoryRegionsCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d3f67-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>
<span data-ttu-id="d3f67-103">Poskytuje metodu zpětného volání pro [iclrdataenummemoryregions::enummemoryregions –](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) k poskytnutí zprávy ladicímu programu výsledek pokusu o výčet určité oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="d3f67-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d3f67-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d3f67-104">Methods</span></span>  
  
|<span data-ttu-id="d3f67-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d3f67-105">Method</span></span>|<span data-ttu-id="d3f67-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d3f67-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d3f67-107">EnumMemoryRegion – metoda</span><span class="sxs-lookup"><span data-stu-id="d3f67-107">EnumMemoryRegion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="d3f67-108">Volané `ICLRDataEnumMemoryRegions::EnumMemoryRegions` k poskytnutí zprávy ladicímu programu výsledek pokusu o výčet určité oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="d3f67-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d3f67-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d3f67-109">Requirements</span></span>  
 <span data-ttu-id="d3f67-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3f67-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3f67-111">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="d3f67-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="d3f67-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3f67-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3f67-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3f67-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3f67-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d3f67-114">See also</span></span>

- [<span data-ttu-id="d3f67-115">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="d3f67-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
