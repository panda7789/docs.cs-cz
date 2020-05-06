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
ms.openlocfilehash: e6cdc924df126e56d2e7c8c9cb8762ee88712fcc
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860699"
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a><span data-ttu-id="494af-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions – metoda</span><span class="sxs-lookup"><span data-stu-id="494af-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions Method</span></span>
<span data-ttu-id="494af-103">Vytvoří výčet zadaných oblastí paměti.</span><span class="sxs-lookup"><span data-stu-id="494af-103">Enumerates specified areas of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="494af-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="494af-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="494af-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="494af-105">Parameters</span></span>  
 `callback`  
 <span data-ttu-id="494af-106">pro Ukazatel na instanci [ICLRDataEnumMemoryRegionsCallback –](iclrdataenummemoryregionscallback-interface.md) , která je volána touto metodou pro každou oblast paměti, která je vyčíslena pro oznamování ladicímu programu výsledku.</span><span class="sxs-lookup"><span data-stu-id="494af-106">[in] A pointer to an [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) instance that is called by this method for each memory region being enumerated to notify the debugger of the result.</span></span>  
  
 <span data-ttu-id="494af-107">Výčet oblastí paměti pokračuje i v případě, že zpětné volání signalizuje selhání.</span><span class="sxs-lookup"><span data-stu-id="494af-107">The enumeration of memory regions continues even if the callback indicates a failure.</span></span>  
  
 `miniDumpFlags`  
 <span data-ttu-id="494af-108">pro Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="494af-108">[in] Not used.</span></span>  
  
 `clrFlags`  
 <span data-ttu-id="494af-109">pro Hodnota výčtu [CLRDataEnumMemoryFlags –](clrdataenummemoryflags-enumeration.md) , která určuje oblasti paměti, které mají být vyčísleny.</span><span class="sxs-lookup"><span data-stu-id="494af-109">[in] A value of the [CLRDataEnumMemoryFlags](clrdataenummemoryflags-enumeration.md) enumeration that specifies the regions of memory to be enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="494af-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="494af-110">Remarks</span></span>  
 <span data-ttu-id="494af-111">Tato metoda používá zadanou instanci [ICLRDataEnumMemoryRegionsCallback –](iclrdataenummemoryregionscallback-interface.md) k upozorňování volajícího výsledku.</span><span class="sxs-lookup"><span data-stu-id="494af-111">This method uses the specified [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) instance to notify the caller of results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="494af-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="494af-112">Requirements</span></span>  
 <span data-ttu-id="494af-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="494af-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="494af-114">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="494af-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="494af-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="494af-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="494af-116">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="494af-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="494af-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="494af-117">See also</span></span>

- [<span data-ttu-id="494af-118">ICLRDataEnumMemoryRegions – rozhraní</span><span class="sxs-lookup"><span data-stu-id="494af-118">ICLRDataEnumMemoryRegions Interface</span></span>](iclrdataenummemoryregions-interface.md)
