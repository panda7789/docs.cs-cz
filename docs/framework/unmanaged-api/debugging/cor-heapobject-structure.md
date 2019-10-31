---
title: COR_HEAPOBJECT – struktura
ms.date: 03/30/2017
api_name:
- COR_HEAPOBJECT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPOBJECT
helpviewer_keywords:
- COR_HEAPOBJECT structure [.NET Framework debugging]
ms.assetid: a92fdf95-492b-49ae-a741-2186e5c1d7c5
topic_type:
- apiref
ms.openlocfilehash: 270360a8950197eca14e02a60554659e5ac7b91c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099081"
---
# <a name="cor_heapobject-structure"></a><span data-ttu-id="9fa39-102">COR_HEAPOBJECT – struktura</span><span class="sxs-lookup"><span data-stu-id="9fa39-102">COR_HEAPOBJECT Structure</span></span>
<span data-ttu-id="9fa39-103">Poskytuje informace o objektu na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="9fa39-103">Provides information about an object on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fa39-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9fa39-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;    
    ULONG64 size;             
    COR_TYPEID type;          
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a><span data-ttu-id="9fa39-105">Členové</span><span class="sxs-lookup"><span data-stu-id="9fa39-105">Members</span></span>  
  
|<span data-ttu-id="9fa39-106">Člen</span><span class="sxs-lookup"><span data-stu-id="9fa39-106">Member</span></span>|<span data-ttu-id="9fa39-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9fa39-107">Description</span></span>|  
|------------|-----------------|  
|`address`|<span data-ttu-id="9fa39-108">Adresa objektu v paměti.</span><span class="sxs-lookup"><span data-stu-id="9fa39-108">The address of the object in memory.</span></span>|  
|`size`|<span data-ttu-id="9fa39-109">Celková velikost objektu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="9fa39-109">The total size of the object, in bytes.</span></span>|  
|`type`|<span data-ttu-id="9fa39-110">Token [COR_TYPEID](cor-typeid-structure.md) , který představuje typ objektu.</span><span class="sxs-lookup"><span data-stu-id="9fa39-110">A [COR_TYPEID](cor-typeid-structure.md) token that represents the type of the object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9fa39-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9fa39-111">Remarks</span></span>  
 <span data-ttu-id="9fa39-112">instance `COR_HEAPOBJECT` lze načíst vytvořením výčtu objektu rozhraní [ICorDebugHeapEnum –](icordebugheapenum-interface.md) , který je vyplněn voláním metody [ICorDebugProcess5:: EnumerateHeap –](icordebugprocess5-enumerateheap-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9fa39-112">`COR_HEAPOBJECT` instances can be retrieved by enumerating an [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object that is populated by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span>  
  
 <span data-ttu-id="9fa39-113">Instance `COR_HEAPOBJECT` poskytuje informace buď o živém objektu na spravované haldě, nebo o objektu, který není rootem žádného objektu, ale ještě nebyl shromážděn systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="9fa39-113">A `COR_HEAPOBJECT` instance provides information either about a live object on the managed heap, or about an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span>  
  
 <span data-ttu-id="9fa39-114">Pro lepší výkon je pole `COR_HEAPOBJECT.address` `CORDB_ADDRESS` hodnota, nikoli hodnota rozhraní ICorDebugValue, která se používá v podstatě rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="9fa39-114">For better performance, the `COR_HEAPOBJECT.address` field is a `CORDB_ADDRESS` value rather than the ICorDebugValue interface value used in much of the debugging API.</span></span> <span data-ttu-id="9fa39-115">Chcete-li získat objekt ICorDebugValue pro danou adresu objektu, můžete předat `CORDB_ADDRESS` hodnotu metodě [ICorDebugProcess5:: GetObject](icordebugprocess5-getobject-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9fa39-115">To obtain an ICorDebugValue object for a given object address, you can pass the `CORDB_ADDRESS` value to the [ICorDebugProcess5::GetObject](icordebugprocess5-getobject-method.md) method.</span></span>  
  
 <span data-ttu-id="9fa39-116">Pro lepší výkon je pole `COR_HEAPOBJECT.type` `COR_TYPEID` hodnota, nikoli hodnota rozhraní ICorDebugType, která se používá v podstatě rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="9fa39-116">For better performance, the `COR_HEAPOBJECT.type` field is a `COR_TYPEID` value rather than the ICorDebugType interface value used in much of the debugging API.</span></span> <span data-ttu-id="9fa39-117">Chcete-li získat objekt ICorDebugType pro daný typ ID, můžete předat `COR_TYPEID` hodnotu metodě [ICorDebugProcess5:: GetTypeForTypeID –](icordebugprocess5-gettypefortypeid-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9fa39-117">To obtain an ICorDebugType object for a given type ID, you can pass the `COR_TYPEID` value to the [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) method.</span></span>  
  
 <span data-ttu-id="9fa39-118">Struktura `COR_HEAPOBJECT` zahrnuje rozhraní COM s vypočítáným odkazem.</span><span class="sxs-lookup"><span data-stu-id="9fa39-118">The `COR_HEAPOBJECT` structure includes a reference-counted COM interface.</span></span> <span data-ttu-id="9fa39-119">Pokud načtete instanci `COR_HEAPOBJECT` z čítače voláním metody [ICorDebugHeapEnum –:: Next](icordebugheapenum-next-method.md) , je nutné odkaz vydat následně.</span><span class="sxs-lookup"><span data-stu-id="9fa39-119">If you retrieve a `COR_HEAPOBJECT` instance from the enumerator by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method, you must subsequently release the reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fa39-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9fa39-120">Requirements</span></span>  
 <span data-ttu-id="9fa39-121">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fa39-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fa39-122">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9fa39-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9fa39-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9fa39-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9fa39-124">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fa39-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fa39-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9fa39-125">See also</span></span>

- [<span data-ttu-id="9fa39-126">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="9fa39-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="9fa39-127">Ladění</span><span class="sxs-lookup"><span data-stu-id="9fa39-127">Debugging</span></span>](index.md)
