---
title: ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion – metoda
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegionsCallback.EnumMemoryRegion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion
helpviewer_keywords:
- EnumMemoryRegion method [.NET Framework debugging]
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion method [.NET Framework debugging]
ms.assetid: 9bb93fab-57e8-4f9a-9ef3-1794504fa896
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85b1c5455cb2008a352461d6b506e43fcef48d17
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59130920"
---
# <a name="iclrdataenummemoryregionscallbackenummemoryregion-method"></a><span data-ttu-id="3c0f6-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion – metoda</span><span class="sxs-lookup"><span data-stu-id="3c0f6-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Method</span></span>
<span data-ttu-id="3c0f6-103">Volané [iclrdataenummemoryregions::enummemoryregions –](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) k poskytnutí zprávy ladicímu programu výsledek pokusu o výčet určité oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="3c0f6-103">Called by [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c0f6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c0f6-104">Syntax</span></span>  
  
```  
HRESULT EnumMemoryRegion (  
    [in] CLRDATA_ADDRESS  address,  
    [in] ULONG32          size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c0f6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3c0f6-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="3c0f6-106">[in] Počáteční adresa, která byla pro provedení výčtu oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="3c0f6-106">[in] The starting address of the memory region that was to be enumerated.</span></span>  
  
 `size`  
 <span data-ttu-id="3c0f6-107">[in] Velikost v bajtech, oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="3c0f6-107">[in] The size, in bytes, of the memory region.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c0f6-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3c0f6-108">Remarks</span></span>  
 <span data-ttu-id="3c0f6-109">`ICLRDataEnumMemoryRegions::EnumMemoryRegions` Metoda zavolá tato metoda zpětného volání po každém pokusu o výčet oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="3c0f6-109">The `ICLRDataEnumMemoryRegions::EnumMemoryRegions` method will call this callback method after each attempt to enumerate a memory region.</span></span> <span data-ttu-id="3c0f6-110">Výčet pokračovat i v případě, že tato metoda vrátí hodnotu HRESULT označující selhání.</span><span class="sxs-lookup"><span data-stu-id="3c0f6-110">The enumeration will continue even if this method returns an HRESULT indicating failure.</span></span>  
  
 <span data-ttu-id="3c0f6-111">Oblasti hlášených toto zpětné volání může být duplicitní nebo překrývající se oblasti.</span><span class="sxs-lookup"><span data-stu-id="3c0f6-111">Regions reported by this callback may be duplicates or overlapping regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c0f6-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3c0f6-112">Requirements</span></span>  
 <span data-ttu-id="3c0f6-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c0f6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c0f6-114">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="3c0f6-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="3c0f6-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c0f6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c0f6-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c0f6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c0f6-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3c0f6-117">See also</span></span>

- [<span data-ttu-id="3c0f6-118">ICLRDataEnumMemoryRegionsCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3c0f6-118">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)
