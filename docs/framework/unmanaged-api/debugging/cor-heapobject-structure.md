---
title: "COR_HEAPOBJECT – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_HEAPOBJECT
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_HEAPOBJECT
helpviewer_keywords: COR_HEAPOBJECT structure [.NET Framework debugging]
ms.assetid: a92fdf95-492b-49ae-a741-2186e5c1d7c5
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 476d9dcb1c6700833b0a113028bdaaf0c5a375c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corheapobject-structure"></a><span data-ttu-id="4980d-102">COR_HEAPOBJECT – struktura</span><span class="sxs-lookup"><span data-stu-id="4980d-102">COR_HEAPOBJECT Structure</span></span>
<span data-ttu-id="4980d-103">Poskytuje informace o objekt na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="4980d-103">Provides information about an object on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4980d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4980d-104">Syntax</span></span>  
  
```  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;    
    ULONG64 size;             
    COR_TYPEID type;          
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a><span data-ttu-id="4980d-105">Členové</span><span class="sxs-lookup"><span data-stu-id="4980d-105">Members</span></span>  
  
|<span data-ttu-id="4980d-106">Člen</span><span class="sxs-lookup"><span data-stu-id="4980d-106">Member</span></span>|<span data-ttu-id="4980d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4980d-107">Description</span></span>|  
|------------|-----------------|  
|`address`|<span data-ttu-id="4980d-108">Adresa objektu v paměti.</span><span class="sxs-lookup"><span data-stu-id="4980d-108">The address of the object in memory.</span></span>|  
|`size`|<span data-ttu-id="4980d-109">Celková velikost objektu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="4980d-109">The total size of the object, in bytes.</span></span>|  
|`type`|<span data-ttu-id="4980d-110">A [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token, který představuje typ objektu.</span><span class="sxs-lookup"><span data-stu-id="4980d-110">A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that represents the type of the object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4980d-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4980d-111">Remarks</span></span>  
 <span data-ttu-id="4980d-112">`COR_HEAPOBJECT`může načíst vytváření výčtu instancí [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) rozhraní objekt, který je vyplněný voláním [icordebugprocess5::enumerateheap –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="4980d-112">`COR_HEAPOBJECT` instances can be retrieved by enumerating an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object that is populated by calling the [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) method.</span></span>  
  
 <span data-ttu-id="4980d-113">A `COR_HEAPOBJECT` instance poskytuje informace o objekt za provozu na spravovaná halda nebo o objekt, který není root pomocí libovolného objektu, ale nebyla ještě zjištěna modulem garbage collector.</span><span class="sxs-lookup"><span data-stu-id="4980d-113">A `COR_HEAPOBJECT` instance provides information either about a live object on the managed heap, or about an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span>  
  
 <span data-ttu-id="4980d-114">Pro lepší výkon `COR_HEAPOBJECT.address` pole `CORDB_ADDRESS` hodnota než ICorDebugValue rozhraní hodnoty používané prakticky rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="4980d-114">For better performance, the `COR_HEAPOBJECT.address` field is a `CORDB_ADDRESS` value rather than the ICorDebugValue interface value used in much of the debugging API.</span></span> <span data-ttu-id="4980d-115">Pokud chcete získat objekt ICorDebugValue pro daný objekt adresu, můžete předat `CORDB_ADDRESS` hodnotu [icordebugprocess5::GetObject –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="4980d-115">To obtain an ICorDebugValue object for a given object address, you can pass the `CORDB_ADDRESS` value to the [ICorDebugProcess5::GetObject](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md) method.</span></span>  
  
 <span data-ttu-id="4980d-116">Pro lepší výkon `COR_HEAPOBJECT.type` pole `COR_TYPEID` hodnota než ICorDebugType rozhraní hodnoty používané prakticky rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="4980d-116">For better performance, the `COR_HEAPOBJECT.type` field is a `COR_TYPEID` value rather than the ICorDebugType interface value used in much of the debugging API.</span></span> <span data-ttu-id="4980d-117">Získat ICorDebugType objekt daného typu ID, abyste mohli předávat `COR_TYPEID` hodnotu [icordebugprocess5::gettypefortypeid –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="4980d-117">To obtain an ICorDebugType object for a given type ID, you can pass the `COR_TYPEID` value to the [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) method.</span></span>  
  
 <span data-ttu-id="4980d-118">`COR_HEAPOBJECT` Struktura zahrnuje rozhraní modelu COM počítá odkaz.</span><span class="sxs-lookup"><span data-stu-id="4980d-118">The `COR_HEAPOBJECT` structure includes a reference-counted COM interface.</span></span> <span data-ttu-id="4980d-119">Pokud je načíst `COR_HEAPOBJECT` instance z enumerátor voláním [icordebugheapenum::Next –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) metoda, je nutné uvolnit následně odkaz na.</span><span class="sxs-lookup"><span data-stu-id="4980d-119">If you retrieve a `COR_HEAPOBJECT` instance from the enumerator by calling the [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) method, you must subsequently release the reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4980d-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4980d-120">Requirements</span></span>  
 <span data-ttu-id="4980d-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4980d-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4980d-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4980d-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4980d-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4980d-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4980d-124">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4980d-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4980d-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="4980d-125">See Also</span></span>  
 [<span data-ttu-id="4980d-126">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="4980d-126">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="4980d-127">Ladění</span><span class="sxs-lookup"><span data-stu-id="4980d-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
