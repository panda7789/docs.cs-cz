---
title: ICorDebugProcess5::EnumerateHeapRegions – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeapRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeapRegions
helpviewer_keywords:
- EnumerateHeapRegions method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeapRegions method [.NET Framework debugging]
ms.assetid: b1edba68-9c36-4f69-be9f-678ce0b33480
topic_type:
- apiref
ms.openlocfilehash: 8070b0693b5718ad8b4cbeb9bf5792cb7f4a0a85
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792395"
---
# <a name="icordebugprocess5enumerateheapregions-method"></a><span data-ttu-id="c3137-102">ICorDebugProcess5::EnumerateHeapRegions – metoda</span><span class="sxs-lookup"><span data-stu-id="c3137-102">ICorDebugProcess5::EnumerateHeapRegions Method</span></span>
<span data-ttu-id="c3137-103">Získá enumerátor pro rozsahy paměti spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="c3137-103">Gets an enumerator for the memory ranges of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3137-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3137-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3137-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c3137-105">Parameters</span></span>  
 `ppRegions`  
 <span data-ttu-id="c3137-106">mimo Ukazatel na adresu objektu rozhraní [ICorDebugHeapSegmentEnum –](icordebugheapsegmentenum-interface.md) , který je enumerátorem pro rozsahy paměti, ve které se objekty nacházejí ve spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="c3137-106">[out] A pointer to the address of an [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) interface object that is an enumerator for the ranges of memory in which objects reside in the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3137-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c3137-107">Remarks</span></span>  
 <span data-ttu-id="c3137-108">Před voláním metody `ICorDebugProcess5::EnumerateHeapRegions` byste měli zavolat metodu [ICorDebugProcess5:: GetGCHeapInformation –](icordebugprocess5-getgcheapinformation-method.md) a zkontrolovat hodnotu pole `areGCStructuresValid` vráceného objektu [COR_HEAPINFO](cor-heapinfo-structure.md) , abyste zajistili, že halda uvolňování paměti v aktuálním stavu je vyčíslitelné.</span><span class="sxs-lookup"><span data-stu-id="c3137-108">Before calling the `ICorDebugProcess5::EnumerateHeapRegions` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="c3137-109">Kromě toho metoda `ICorDebugProcess5::EnumerateHeapRegions` vrátí `E_FAIL`, pokud se připojíte příliš brzy během životnosti procesu, před vytvořením oblastí paměti.</span><span class="sxs-lookup"><span data-stu-id="c3137-109">In addition, the `ICorDebugProcess5::EnumerateHeapRegions` method returns `E_FAIL` if you attach too early in the lifetime of the process, before memory regions are created.</span></span>  
  
 <span data-ttu-id="c3137-110">Tato metoda zaručuje výčet všech oblastí paměti, které mohou obsahovat spravované objekty, ale nezaručuje, že se spravované objekty skutečně nacházejí v těchto oblastech.</span><span class="sxs-lookup"><span data-stu-id="c3137-110">This method is guaranteed to enumerate all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="c3137-111">Objekt kolekce [ICorDebugHeapSegmentEnum –](icordebugheapsegmentenum-interface.md) může zahrnovat prázdné nebo rezervované oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="c3137-111">The [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) collection object may include empty or reserved memory regions.</span></span>  
  
 <span data-ttu-id="c3137-112">Objekt rozhraní [ICorDebugHeapSegmentEnum –](icordebugheapsegmentenum-interface.md) je standardní enumerátor odvozený z rozhraní ICorDebugEnum, které umožňuje vytvořit výčet objektů [COR_SEGMENT](cor-segment-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="c3137-112">The [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_SEGMENT](cor-segment-structure.md) objects.</span></span> <span data-ttu-id="c3137-113">Každý objekt [COR_SEGMENT](cor-segment-structure.md) poskytuje informace o rozsahu paměti konkrétního segmentu spolu s generováním objektů v tomto segmentu.</span><span class="sxs-lookup"><span data-stu-id="c3137-113">Each [COR_SEGMENT](cor-segment-structure.md) object provides information about the memory range of a particular segment, along with the generation of the objects in that segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3137-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c3137-114">Requirements</span></span>  
 <span data-ttu-id="c3137-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3137-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3137-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c3137-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3137-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c3137-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3137-118">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3137-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3137-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c3137-119">See also</span></span>

- [<span data-ttu-id="c3137-120">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c3137-120">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="c3137-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="c3137-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
