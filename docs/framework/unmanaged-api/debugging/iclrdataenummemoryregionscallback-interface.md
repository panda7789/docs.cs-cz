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
ms.openlocfilehash: ddcb8064dfb9be30c66404a8762a9ca73cd6afe4
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860659"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="8c968-102">ICLRDataEnumMemoryRegionsCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8c968-102">ICLRDataEnumMemoryRegionsCallback Interface</span></span>
<span data-ttu-id="8c968-103">Poskytuje metodu zpětného volání pro [ICLRDataEnumMemoryRegions –:: EnumMemoryRegions –](iclrdataenummemoryregions-enummemoryregions-method.md) , která oznamuje ladicímu programu výsledek pokusu o vytvoření výčtu konkrétní oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="8c968-103">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8c968-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8c968-104">Methods</span></span>  
  
|<span data-ttu-id="8c968-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8c968-105">Method</span></span>|<span data-ttu-id="8c968-106">Popis</span><span class="sxs-lookup"><span data-stu-id="8c968-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8c968-107">EnumMemoryRegion – metoda</span><span class="sxs-lookup"><span data-stu-id="8c968-107">EnumMemoryRegion Method</span></span>](iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="8c968-108">Volá `ICLRDataEnumMemoryRegions::EnumMemoryRegions` se, aby se do ladicího programu nahlásila výsledek pokusu o vytvoření výčtu konkrétní oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="8c968-108">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8c968-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8c968-109">Requirements</span></span>  
 <span data-ttu-id="8c968-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c968-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c968-111">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="8c968-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="8c968-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8c968-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c968-113">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c968-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c968-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="8c968-114">See also</span></span>

- [<span data-ttu-id="8c968-115">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8c968-115">Debugging Interfaces</span></span>](debugging-interfaces.md)
