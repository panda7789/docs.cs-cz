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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f179b58ff8eb51e2843780d3212cf38ed7d13216
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168828"
---
# <a name="corheapobject-structure"></a><span data-ttu-id="6d294-102">COR_HEAPOBJECT – struktura</span><span class="sxs-lookup"><span data-stu-id="6d294-102">COR_HEAPOBJECT Structure</span></span>
<span data-ttu-id="6d294-103">Poskytuje informace o objektu na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="6d294-103">Provides information about an object on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d294-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d294-104">Syntax</span></span>  
  
```  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;    
    ULONG64 size;             
    COR_TYPEID type;          
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a><span data-ttu-id="6d294-105">Členové</span><span class="sxs-lookup"><span data-stu-id="6d294-105">Members</span></span>  
  
|<span data-ttu-id="6d294-106">Člen</span><span class="sxs-lookup"><span data-stu-id="6d294-106">Member</span></span>|<span data-ttu-id="6d294-107">Popis</span><span class="sxs-lookup"><span data-stu-id="6d294-107">Description</span></span>|  
|------------|-----------------|  
|`address`|<span data-ttu-id="6d294-108">Adresa objektu v paměti.</span><span class="sxs-lookup"><span data-stu-id="6d294-108">The address of the object in memory.</span></span>|  
|`size`|<span data-ttu-id="6d294-109">Celková velikost objektu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="6d294-109">The total size of the object, in bytes.</span></span>|  
|`type`|<span data-ttu-id="6d294-110">A [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token, který představuje typ objektu.</span><span class="sxs-lookup"><span data-stu-id="6d294-110">A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that represents the type of the object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d294-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6d294-111">Remarks</span></span>  
 <span data-ttu-id="6d294-112">`COR_HEAPOBJECT` instance je možné načíst podle výčet [icordebugheapenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) rozhraní objektu, který je vyplněný voláním [icordebugprocess5::enumerateheap –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="6d294-112">`COR_HEAPOBJECT` instances can be retrieved by enumerating an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object that is populated by calling the [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) method.</span></span>  
  
 <span data-ttu-id="6d294-113">A `COR_HEAPOBJECT` instance obsahuje informace o objektu na spravované haldě za provozu nebo o objekt, který není uveden do kořene s jakýmkoli objektem, ale nebyl dosud shromažďuje systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6d294-113">A `COR_HEAPOBJECT` instance provides information either about a live object on the managed heap, or about an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span>  
  
 <span data-ttu-id="6d294-114">Pro zajištění lepšího výkonu `COR_HEAPOBJECT.address` je pole `CORDB_ADDRESS` hodnotu, nikoli icordebugvalue – rozhraní hodnota použitá v velkou část rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="6d294-114">For better performance, the `COR_HEAPOBJECT.address` field is a `CORDB_ADDRESS` value rather than the ICorDebugValue interface value used in much of the debugging API.</span></span> <span data-ttu-id="6d294-115">K získání objektu ICorDebugValue pro daný objekt adresu, můžete předat `CORDB_ADDRESS` hodnota, která se [icordebugprocess5::GetObject –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="6d294-115">To obtain an ICorDebugValue object for a given object address, you can pass the `CORDB_ADDRESS` value to the [ICorDebugProcess5::GetObject](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md) method.</span></span>  
  
 <span data-ttu-id="6d294-116">Pro zajištění lepšího výkonu `COR_HEAPOBJECT.type` je pole `COR_TYPEID` hodnotu, nikoli icordebugtype – rozhraní hodnota použitá v velkou část rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="6d294-116">For better performance, the `COR_HEAPOBJECT.type` field is a `COR_TYPEID` value rather than the ICorDebugType interface value used in much of the debugging API.</span></span> <span data-ttu-id="6d294-117">Získat ICorDebugType objekt daného typu ID, můžete předat `COR_TYPEID` hodnota, která se [icordebugprocess5::gettypefortypeid –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="6d294-117">To obtain an ICorDebugType object for a given type ID, you can pass the `COR_TYPEID` value to the [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) method.</span></span>  
  
 <span data-ttu-id="6d294-118">`COR_HEAPOBJECT` Struktura zahrnuje rozhraní modelu COM počítaného odkazy.</span><span class="sxs-lookup"><span data-stu-id="6d294-118">The `COR_HEAPOBJECT` structure includes a reference-counted COM interface.</span></span> <span data-ttu-id="6d294-119">Pokud načtete `COR_HEAPOBJECT` instanci z výčtu voláním [icordebugheapenum::Next –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) metoda, následně nutné uvolnit odkaz.</span><span class="sxs-lookup"><span data-stu-id="6d294-119">If you retrieve a `COR_HEAPOBJECT` instance from the enumerator by calling the [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) method, you must subsequently release the reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d294-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6d294-120">Requirements</span></span>  
 <span data-ttu-id="6d294-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d294-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d294-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d294-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d294-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d294-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d294-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d294-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d294-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6d294-125">See also</span></span>

- [<span data-ttu-id="6d294-126">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="6d294-126">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="6d294-127">Ladění</span><span class="sxs-lookup"><span data-stu-id="6d294-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
