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
ms.openlocfilehash: 693ec07176f80711709cd9b85c6886bea8be74b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122970"
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a><span data-ttu-id="162b8-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions – metoda</span><span class="sxs-lookup"><span data-stu-id="162b8-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions Method</span></span>
<span data-ttu-id="162b8-103">Vytvoří výčet zadaných oblastí paměti.</span><span class="sxs-lookup"><span data-stu-id="162b8-103">Enumerates specified areas of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="162b8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="162b8-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="162b8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="162b8-105">Parameters</span></span>  
 `callback`  
 <span data-ttu-id="162b8-106">pro Ukazatel na instanci [ICLRDataEnumMemoryRegionsCallback –](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) , která je volána touto metodou pro každou oblast paměti, která je vyčíslena pro oznamování ladicímu programu výsledku.</span><span class="sxs-lookup"><span data-stu-id="162b8-106">[in] A pointer to an [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance that is called by this method for each memory region being enumerated to notify the debugger of the result.</span></span>  
  
 <span data-ttu-id="162b8-107">Výčet oblastí paměti pokračuje i v případě, že zpětné volání signalizuje selhání.</span><span class="sxs-lookup"><span data-stu-id="162b8-107">The enumeration of memory regions continues even if the callback indicates a failure.</span></span>  
  
 `miniDumpFlags`  
 <span data-ttu-id="162b8-108">pro Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="162b8-108">[in] Not used.</span></span>  
  
 `clrFlags`  
 <span data-ttu-id="162b8-109">pro Hodnota výčtu [CLRDataEnumMemoryFlags –](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) , která určuje oblasti paměti, které mají být vyčísleny.</span><span class="sxs-lookup"><span data-stu-id="162b8-109">[in] A value of the [CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) enumeration that specifies the regions of memory to be enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="162b8-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="162b8-110">Remarks</span></span>  
 <span data-ttu-id="162b8-111">Tato metoda používá zadanou instanci [ICLRDataEnumMemoryRegionsCallback –](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) k upozorňování volajícího výsledku.</span><span class="sxs-lookup"><span data-stu-id="162b8-111">This method uses the specified [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance to notify the caller of results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="162b8-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="162b8-112">Requirements</span></span>  
 <span data-ttu-id="162b8-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="162b8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="162b8-114">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="162b8-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="162b8-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="162b8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="162b8-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="162b8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="162b8-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="162b8-117">See also</span></span>

- [<span data-ttu-id="162b8-118">ICLRDataEnumMemoryRegions – rozhraní</span><span class="sxs-lookup"><span data-stu-id="162b8-118">ICLRDataEnumMemoryRegions Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)
