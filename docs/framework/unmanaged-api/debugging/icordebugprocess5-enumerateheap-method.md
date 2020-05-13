---
title: ICorDebugProcess5::EnumerateHeap – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeap
helpviewer_keywords:
- EnumerateHeap method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeap method [.NET Framework debugging]
ms.assetid: b0192104-6073-4089-a4df-dc29ee033074
topic_type:
- apiref
ms.openlocfilehash: 9386c77cc98df17d797d5886e1603ffc4824b6dc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205238"
---
# <a name="icordebugprocess5enumerateheap-method"></a><span data-ttu-id="761a7-102">ICorDebugProcess5::EnumerateHeap – metoda</span><span class="sxs-lookup"><span data-stu-id="761a7-102">ICorDebugProcess5::EnumerateHeap Method</span></span>
<span data-ttu-id="761a7-103">Získá enumerátor pro objekty na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="761a7-103">Gets an enumerator for the objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="761a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="761a7-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="761a7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="761a7-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="761a7-106">mimo Ukazatel na adresu objektu rozhraní [ICorDebugHeapEnum –](icordebugheapenum-interface.md) , který je enumerátorem pro objekty, které jsou umístěny na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="761a7-106">[out] A pointer to the address of an [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object that is an enumerator for the objects that reside on the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="761a7-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="761a7-107">Remarks</span></span>  
 <span data-ttu-id="761a7-108">Před voláním `ICorDebugProcess5::EnumerateHeap` metody byste měli zavolat metodu [ICorDebugProcess5:: GetGCHeapInformation –](icordebugprocess5-getgcheapinformation-method.md) a zkontrolovat hodnotu `areGCStructuresValid` pole vráceného objektu [COR_HEAPINFO](cor-heapinfo-structure.md) , aby se zajistilo, že halda uvolňování paměti v jejím aktuálním stavu je vyčíslitelné.</span><span class="sxs-lookup"><span data-stu-id="761a7-108">Before calling the `ICorDebugProcess5::EnumerateHeap` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="761a7-109">Kromě toho se `ICorDebugProcess5::EnumerateHeap` vrátí, `E_FAIL` Pokud se připojíte příliš brzy během životnosti procesu, než se přidělí paměť pro spravovanou haldu.</span><span class="sxs-lookup"><span data-stu-id="761a7-109">In addition, the `ICorDebugProcess5::EnumerateHeap` returns `E_FAIL` if you attach too early in the lifetime of the process, before memory for the managed heap is allocated.</span></span>  
  
 <span data-ttu-id="761a7-110">Objekt rozhraní [ICorDebugHeapEnum –](icordebugheapenum-interface.md) je standardní enumerátor odvozený z rozhraní ICorDebugEnum, které umožňuje vytvořit výčet objektů [COR_HEAPOBJECT](cor-heapobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="761a7-110">The [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_HEAPOBJECT](cor-heapobject-structure.md) objects.</span></span> <span data-ttu-id="761a7-111">Tato metoda naplní objekt kolekce [ICorDebugHeapEnum –](icordebugheapenum-interface.md) instancemi [COR_HEAPOBJECT](cor-heapobject-structure.md) , které poskytují informace o všech objektech.</span><span class="sxs-lookup"><span data-stu-id="761a7-111">This method populates the [ICorDebugHeapEnum](icordebugheapenum-interface.md) collection object with [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that provide information about all objects.</span></span> <span data-ttu-id="761a7-112">Kolekce může také zahrnovat [COR_HEAPOBJECT](cor-heapobject-structure.md) instance, které poskytují informace o objektech, které nejsou rootem žádného objektu, ale ještě nebyly shromážděny systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="761a7-112">The collection may also include [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that provide information about objects that are not rooted by any object but have not yet been collected by the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="761a7-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="761a7-113">Requirements</span></span>  
 <span data-ttu-id="761a7-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="761a7-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="761a7-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="761a7-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="761a7-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="761a7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="761a7-117">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="761a7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="761a7-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="761a7-118">See also</span></span>

- [<span data-ttu-id="761a7-119">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="761a7-119">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="761a7-120">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="761a7-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
