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
ms.openlocfilehash: 0a0af0c86bc44a4968119e1afd2a84e17e941601
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405496"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="d0910-102">ICLRDataEnumMemoryRegionsCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0910-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>
<span data-ttu-id="d0910-103">Poskytuje metody zpětného volání pro [iclrdataenummemoryregions::enummemoryregions –](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) tak, aby odesílaly ladicího programu výsledek pokusu o zobrazení výčtu zadané oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="d0910-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d0910-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d0910-104">Methods</span></span>  
  
|<span data-ttu-id="d0910-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d0910-105">Method</span></span>|<span data-ttu-id="d0910-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d0910-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d0910-107">EnumMemoryRegion – metoda</span><span class="sxs-lookup"><span data-stu-id="d0910-107">EnumMemoryRegion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="d0910-108">Voláno rozhraním `ICLRDataEnumMemoryRegions::EnumMemoryRegions` tak, aby odesílaly ladicího programu výsledek pokusu o zobrazení výčtu zadané oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="d0910-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d0910-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d0910-109">Requirements</span></span>  
 <span data-ttu-id="d0910-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0910-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0910-111">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="d0910-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="d0910-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0910-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0910-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0910-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0910-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0910-114">See Also</span></span>  
 [<span data-ttu-id="d0910-115">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="d0910-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
