---
title: "ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataEnumMemoryRegionsCallback.EnumMemoryRegion
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion
helpviewer_keywords:
- EnumMemoryRegion method [.NET Framework debugging]
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion method [.NET Framework debugging]
ms.assetid: 9bb93fab-57e8-4f9a-9ef3-1794504fa896
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e1b1897b18a8dcbb261a5041ca8b530b7877b910
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdataenummemoryregionscallbackenummemoryregion-method"></a><span data-ttu-id="2c8e9-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion – metoda</span><span class="sxs-lookup"><span data-stu-id="2c8e9-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Method</span></span>
<span data-ttu-id="2c8e9-103">Voláno rozhraním [iclrdataenummemoryregions::enummemoryregions –](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) tak, aby odesílaly ladicího programu výsledek pokusu o zobrazení výčtu zadané oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="2c8e9-103">Called by [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c8e9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c8e9-104">Syntax</span></span>  
  
```  
HRESULT EnumMemoryRegion (  
    [in] CLRDATA_ADDRESS  address,  
    [in] ULONG32          size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2c8e9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2c8e9-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="2c8e9-106">[v] Počáteční adresa paměti oblast, která se má být proveden.</span><span class="sxs-lookup"><span data-stu-id="2c8e9-106">[in] The starting address of the memory region that was to be enumerated.</span></span>  
  
 `size`  
 <span data-ttu-id="2c8e9-107">[v] Velikost v bajtech, oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="2c8e9-107">[in] The size, in bytes, of the memory region.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c8e9-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2c8e9-108">Remarks</span></span>  
 <span data-ttu-id="2c8e9-109">`ICLRDataEnumMemoryRegions::EnumMemoryRegions` Metoda zavolá tato metoda zpětného volání po každém pokusu o zobrazení výčtu oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="2c8e9-109">The `ICLRDataEnumMemoryRegions::EnumMemoryRegions` method will call this callback method after each attempt to enumerate a memory region.</span></span> <span data-ttu-id="2c8e9-110">Výčet bude pokračovat, i když tato metoda vrátí hodnotu udávající neúspěch HRESULT.</span><span class="sxs-lookup"><span data-stu-id="2c8e9-110">The enumeration will continue even if this method returns an HRESULT indicating failure.</span></span>  
  
 <span data-ttu-id="2c8e9-111">Oblasti hlášené tento zpětného volání může být duplicitní nebo překrývající se oblasti.</span><span class="sxs-lookup"><span data-stu-id="2c8e9-111">Regions reported by this callback may be duplicates or overlapping regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c8e9-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2c8e9-112">Requirements</span></span>  
 <span data-ttu-id="2c8e9-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c8e9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c8e9-114">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="2c8e9-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="2c8e9-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c8e9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c8e9-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c8e9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c8e9-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="2c8e9-117">See Also</span></span>  
 [<span data-ttu-id="2c8e9-118">Iclrdataenummemoryregionscallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2c8e9-118">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)
