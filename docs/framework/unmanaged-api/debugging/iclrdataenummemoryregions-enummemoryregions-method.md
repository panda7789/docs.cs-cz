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
ms.openlocfilehash: f2b2bbe8bcecf71f6d3016fb35dfbf5ba1353aea
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785629"
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a><span data-ttu-id="30436-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions – metoda</span><span class="sxs-lookup"><span data-stu-id="30436-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions Method</span></span>
<span data-ttu-id="30436-103">Vytvoří výčet zadaných oblastí paměti.</span><span class="sxs-lookup"><span data-stu-id="30436-103">Enumerates specified areas of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30436-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30436-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30436-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="30436-105">Parameters</span></span>  
 `callback`  
 <span data-ttu-id="30436-106">pro Ukazatel na instanci [ICLRDataEnumMemoryRegionsCallback –](iclrdataenummemoryregionscallback-interface.md) , která je volána touto metodou pro každou oblast paměti, která je vyčíslena pro oznamování ladicímu programu výsledku.</span><span class="sxs-lookup"><span data-stu-id="30436-106">[in] A pointer to an [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) instance that is called by this method for each memory region being enumerated to notify the debugger of the result.</span></span>  
  
 <span data-ttu-id="30436-107">Výčet oblastí paměti pokračuje i v případě, že zpětné volání signalizuje selhání.</span><span class="sxs-lookup"><span data-stu-id="30436-107">The enumeration of memory regions continues even if the callback indicates a failure.</span></span>  
  
 `miniDumpFlags`  
 <span data-ttu-id="30436-108">pro Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="30436-108">[in] Not used.</span></span>  
  
 `clrFlags`  
 <span data-ttu-id="30436-109">pro Hodnota výčtu [CLRDataEnumMemoryFlags –](clrdataenummemoryflags-enumeration.md) , která určuje oblasti paměti, které mají být vyčísleny.</span><span class="sxs-lookup"><span data-stu-id="30436-109">[in] A value of the [CLRDataEnumMemoryFlags](clrdataenummemoryflags-enumeration.md) enumeration that specifies the regions of memory to be enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30436-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="30436-110">Remarks</span></span>  
 <span data-ttu-id="30436-111">Tato metoda používá zadanou instanci [ICLRDataEnumMemoryRegionsCallback –](iclrdataenummemoryregionscallback-interface.md) k upozorňování volajícího výsledku.</span><span class="sxs-lookup"><span data-stu-id="30436-111">This method uses the specified [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) instance to notify the caller of results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30436-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="30436-112">Requirements</span></span>  
 <span data-ttu-id="30436-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30436-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30436-114">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="30436-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="30436-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="30436-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30436-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30436-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30436-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30436-117">See also</span></span>

- [<span data-ttu-id="30436-118">ICLRDataEnumMemoryRegions – rozhraní</span><span class="sxs-lookup"><span data-stu-id="30436-118">ICLRDataEnumMemoryRegions Interface</span></span>](iclrdataenummemoryregions-interface.md)
