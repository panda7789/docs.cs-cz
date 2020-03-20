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
ms.openlocfilehash: efb3d913e1d8ef0c486d7e5e1d9777ae7d88bc71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179338"
---
# <a name="cor_heapobject-structure"></a><span data-ttu-id="1652b-102">COR_HEAPOBJECT – struktura</span><span class="sxs-lookup"><span data-stu-id="1652b-102">COR_HEAPOBJECT Structure</span></span>
<span data-ttu-id="1652b-103">Obsahuje informace o objektu na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="1652b-103">Provides information about an object on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1652b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1652b-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;
    ULONG64 size;
    COR_TYPEID type;
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a><span data-ttu-id="1652b-105">Členové</span><span class="sxs-lookup"><span data-stu-id="1652b-105">Members</span></span>  
  
|<span data-ttu-id="1652b-106">Člen</span><span class="sxs-lookup"><span data-stu-id="1652b-106">Member</span></span>|<span data-ttu-id="1652b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="1652b-107">Description</span></span>|  
|------------|-----------------|  
|`address`|<span data-ttu-id="1652b-108">Adresa objektu v paměti.</span><span class="sxs-lookup"><span data-stu-id="1652b-108">The address of the object in memory.</span></span>|  
|`size`|<span data-ttu-id="1652b-109">Celková velikost objektu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="1652b-109">The total size of the object, in bytes.</span></span>|  
|`type`|<span data-ttu-id="1652b-110">Token [COR_TYPEID,](cor-typeid-structure.md) který představuje typ objektu.</span><span class="sxs-lookup"><span data-stu-id="1652b-110">A [COR_TYPEID](cor-typeid-structure.md) token that represents the type of the object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1652b-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1652b-111">Remarks</span></span>  
 <span data-ttu-id="1652b-112">`COR_HEAPOBJECT`instance lze načíst výčetem objektu rozhraní [ICorDebugHeapEnum,](icordebugheapenum-interface.md) který je naplněn voláním metody [ICorDebugProcess5::EnumerateHeap.](icordebugprocess5-enumerateheap-method.md)</span><span class="sxs-lookup"><span data-stu-id="1652b-112">`COR_HEAPOBJECT` instances can be retrieved by enumerating an [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object that is populated by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span>  
  
 <span data-ttu-id="1652b-113">Instance `COR_HEAPOBJECT` poskytuje informace o živém objektu na spravované haldě nebo o objektu, který není zakořeněn žádným objektem, ale ještě nebyl shromážděn systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="1652b-113">A `COR_HEAPOBJECT` instance provides information either about a live object on the managed heap, or about an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span>  
  
 <span data-ttu-id="1652b-114">Pro lepší výkon `COR_HEAPOBJECT.address` pole `CORDB_ADDRESS` je hodnota spíše než hodnota rozhraní ICorDebugValue používá ve velké části ladění rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="1652b-114">For better performance, the `COR_HEAPOBJECT.address` field is a `CORDB_ADDRESS` value rather than the ICorDebugValue interface value used in much of the debugging API.</span></span> <span data-ttu-id="1652b-115">Chcete-li získat objekt ICorDebugValue pro danou adresu `CORDB_ADDRESS` objektu, můžete předat hodnotu metodě [ICorDebugProcess5::GetObject.](icordebugprocess5-getobject-method.md)</span><span class="sxs-lookup"><span data-stu-id="1652b-115">To obtain an ICorDebugValue object for a given object address, you can pass the `CORDB_ADDRESS` value to the [ICorDebugProcess5::GetObject](icordebugprocess5-getobject-method.md) method.</span></span>  
  
 <span data-ttu-id="1652b-116">Pro lepší výkon `COR_HEAPOBJECT.type` pole `COR_TYPEID` je hodnota spíše než hodnota rozhraní ICorDebugType používá ve velké části ladění rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="1652b-116">For better performance, the `COR_HEAPOBJECT.type` field is a `COR_TYPEID` value rather than the ICorDebugType interface value used in much of the debugging API.</span></span> <span data-ttu-id="1652b-117">Chcete-li získat objekt ICorDebugType pro dané ID `COR_TYPEID` typu, můžete předat hodnotu metodě [ICorDebugProcess5::GetTypeForTypeID.](icordebugprocess5-gettypefortypeid-method.md)</span><span class="sxs-lookup"><span data-stu-id="1652b-117">To obtain an ICorDebugType object for a given type ID, you can pass the `COR_TYPEID` value to the [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) method.</span></span>  
  
 <span data-ttu-id="1652b-118">`COR_HEAPOBJECT` Struktura obsahuje referenční rozhraní COM.</span><span class="sxs-lookup"><span data-stu-id="1652b-118">The `COR_HEAPOBJECT` structure includes a reference-counted COM interface.</span></span> <span data-ttu-id="1652b-119">Pokud načtete `COR_HEAPOBJECT` instanci z čítače výčtu voláním Metody [ICorDebugHeapEnum::Next,](icordebugheapenum-next-method.md) musíte následně uvolnit odkaz.</span><span class="sxs-lookup"><span data-stu-id="1652b-119">If you retrieve a `COR_HEAPOBJECT` instance from the enumerator by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method, you must subsequently release the reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1652b-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1652b-120">Requirements</span></span>  
 <span data-ttu-id="1652b-121">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1652b-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1652b-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1652b-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1652b-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1652b-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1652b-124">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1652b-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1652b-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="1652b-125">See also</span></span>

- [<span data-ttu-id="1652b-126">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="1652b-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="1652b-127">ladění</span><span class="sxs-lookup"><span data-stu-id="1652b-127">Debugging</span></span>](index.md)
