---
title: ICLRDataEnumMemoryRegions::EnumMemoryRegions – metoda
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegions.EnumMemoryRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions
helpviewer_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions method [.NET Framework debugging]
- EnumMemoryRegions method [.NET Framework debugging]
ms.assetid: 22d2e339-f174-40b5-a478-0b744501566f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 489ea22e17178398f53e103da04a47e8fe15a936
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738931"
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a><span data-ttu-id="45c69-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions – metoda</span><span class="sxs-lookup"><span data-stu-id="45c69-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions Method</span></span>
<span data-ttu-id="45c69-103">Vytvoří výčet zadané oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="45c69-103">Enumerates specified areas of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45c69-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45c69-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45c69-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="45c69-105">Parameters</span></span>  
 `callback`  
 <span data-ttu-id="45c69-106">[in] Ukazatel [iclrdataenummemoryregionscallback –](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instanci, která volá tuto metodu pro každou oblast paměti výčtu oznámit ladicí program výsledku.</span><span class="sxs-lookup"><span data-stu-id="45c69-106">[in] A pointer to an [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance that is called by this method for each memory region being enumerated to notify the debugger of the result.</span></span>  
  
 <span data-ttu-id="45c69-107">Výčet oblastí paměti bude pokračovat i v případě, že zpětné volání naznačuje chybu.</span><span class="sxs-lookup"><span data-stu-id="45c69-107">The enumeration of memory regions continues even if the callback indicates a failure.</span></span>  
  
 `miniDumpFlags`  
 <span data-ttu-id="45c69-108">[in] Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="45c69-108">[in] Not used.</span></span>  
  
 `clrFlags`  
 <span data-ttu-id="45c69-109">[in] Hodnota [clrdataenummemoryflags –](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) výčet, který určuje oblastí paměti pro provedení výčtu.</span><span class="sxs-lookup"><span data-stu-id="45c69-109">[in] A value of the [CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) enumeration that specifies the regions of memory to be enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45c69-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="45c69-110">Remarks</span></span>  
 <span data-ttu-id="45c69-111">Tato metoda používá zadaný [iclrdataenummemoryregionscallback –](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance oznámit volajícímu výsledky.</span><span class="sxs-lookup"><span data-stu-id="45c69-111">This method uses the specified [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance to notify the caller of results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45c69-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="45c69-112">Requirements</span></span>  
 <span data-ttu-id="45c69-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45c69-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45c69-114">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="45c69-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="45c69-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45c69-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45c69-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45c69-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45c69-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="45c69-117">See also</span></span>

- [<span data-ttu-id="45c69-118">ICLRDataEnumMemoryRegions – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45c69-118">ICLRDataEnumMemoryRegions Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)
