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
ms.openlocfilehash: 886f78a0561ebbd5470b7932123f67975d650693
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197344"
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a><span data-ttu-id="2da3b-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions – metoda</span><span class="sxs-lookup"><span data-stu-id="2da3b-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions Method</span></span>
<span data-ttu-id="2da3b-103">Vytvoří výčet zadané oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="2da3b-103">Enumerates specified areas of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2da3b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2da3b-104">Syntax</span></span>  
  
```  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2da3b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2da3b-105">Parameters</span></span>  
 `callback`  
 <span data-ttu-id="2da3b-106">[in] Ukazatel [iclrdataenummemoryregionscallback –](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instanci, která volá tuto metodu pro každou oblast paměti výčtu oznámit ladicí program výsledku.</span><span class="sxs-lookup"><span data-stu-id="2da3b-106">[in] A pointer to an [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance that is called by this method for each memory region being enumerated to notify the debugger of the result.</span></span>  
  
 <span data-ttu-id="2da3b-107">Výčet oblastí paměti bude pokračovat i v případě, že zpětné volání naznačuje chybu.</span><span class="sxs-lookup"><span data-stu-id="2da3b-107">The enumeration of memory regions continues even if the callback indicates a failure.</span></span>  
  
 `miniDumpFlags`  
 <span data-ttu-id="2da3b-108">[in] Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="2da3b-108">[in] Not used.</span></span>  
  
 `clrFlags`  
 <span data-ttu-id="2da3b-109">[in] Hodnota [clrdataenummemoryflags –](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) výčet, který určuje oblastí paměti pro provedení výčtu.</span><span class="sxs-lookup"><span data-stu-id="2da3b-109">[in] A value of the [CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) enumeration that specifies the regions of memory to be enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2da3b-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2da3b-110">Remarks</span></span>  
 <span data-ttu-id="2da3b-111">Tato metoda používá zadaný [iclrdataenummemoryregionscallback –](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance oznámit volajícímu výsledky.</span><span class="sxs-lookup"><span data-stu-id="2da3b-111">This method uses the specified [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance to notify the caller of results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2da3b-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2da3b-112">Requirements</span></span>  
 <span data-ttu-id="2da3b-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2da3b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2da3b-114">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="2da3b-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="2da3b-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2da3b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2da3b-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2da3b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2da3b-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2da3b-117">See also</span></span>

- [<span data-ttu-id="2da3b-118">ICLRDataEnumMemoryRegions – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2da3b-118">ICLRDataEnumMemoryRegions Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)
