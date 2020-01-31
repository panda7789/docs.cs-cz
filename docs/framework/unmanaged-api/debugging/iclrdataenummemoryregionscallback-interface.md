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
ms.openlocfilehash: 4e3891996af5945ed95c8c37dddfee5c446db248
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789112"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="9b207-102">ICLRDataEnumMemoryRegionsCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9b207-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>
<span data-ttu-id="9b207-103">Poskytuje metodu zpětného volání pro [ICLRDataEnumMemoryRegions –:: EnumMemoryRegions –](iclrdataenummemoryregions-enummemoryregions-method.md) , která oznamuje ladicímu programu výsledek pokusu o vytvoření výčtu konkrétní oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="9b207-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9b207-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9b207-104">Methods</span></span>  
  
|<span data-ttu-id="9b207-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9b207-105">Method</span></span>|<span data-ttu-id="9b207-106">Popis</span><span class="sxs-lookup"><span data-stu-id="9b207-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9b207-107">EnumMemoryRegion – metoda</span><span class="sxs-lookup"><span data-stu-id="9b207-107">EnumMemoryRegion Method</span></span>](iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="9b207-108">Volá se `ICLRDataEnumMemoryRegions::EnumMemoryRegions`, aby se nahlásila ladicímu programu v důsledku pokusu o vytvoření výčtu konkrétní oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="9b207-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9b207-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9b207-109">Requirements</span></span>  
 <span data-ttu-id="9b207-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b207-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b207-111">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="9b207-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="9b207-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9b207-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b207-113">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b207-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b207-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9b207-114">See also</span></span>

- [<span data-ttu-id="9b207-115">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="9b207-115">Debugging Interfaces</span></span>](debugging-interfaces.md)
