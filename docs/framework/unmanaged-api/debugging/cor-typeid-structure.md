---
title: COR_TYPEID – struktura
ms.date: 03/30/2017
api_name:
- COR_TYPEID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPEID
helpviewer_keywords:
- COR_TYPEID structure [.NET Framework debugging]
ms.assetid: 1e172b14-ee22-4943-b3b8-3740e7bdcd2e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51104516008ffee0694c72733cb5f82b5ba6d8cf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59109860"
---
# <a name="cortypeid-structure"></a><span data-ttu-id="8b4d4-102">COR_TYPEID – struktura</span><span class="sxs-lookup"><span data-stu-id="8b4d4-102">COR_TYPEID Structure</span></span>
<span data-ttu-id="8b4d4-103">Obsahuje identifikátor typu.</span><span class="sxs-lookup"><span data-stu-id="8b4d4-103">Contains a type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b4d4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b4d4-104">Syntax</span></span>  
  
```  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a><span data-ttu-id="8b4d4-105">Členové</span><span class="sxs-lookup"><span data-stu-id="8b4d4-105">Members</span></span>  
  
|<span data-ttu-id="8b4d4-106">Člen</span><span class="sxs-lookup"><span data-stu-id="8b4d4-106">Member</span></span>|<span data-ttu-id="8b4d4-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8b4d4-107">Description</span></span>|  
|------------|-----------------|  
|`token1`|<span data-ttu-id="8b4d4-108">První token.</span><span class="sxs-lookup"><span data-stu-id="8b4d4-108">The first token.</span></span>|  
|`token2`|<span data-ttu-id="8b4d4-109">Druhý token.</span><span class="sxs-lookup"><span data-stu-id="8b4d4-109">The second token.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b4d4-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8b4d4-110">Remarks</span></span>  
 <span data-ttu-id="8b4d4-111">`COR_TYPEID` Struktura je vrácen počet ladění metody, které poskytují informace o objektech být uvolněna.</span><span class="sxs-lookup"><span data-stu-id="8b4d4-111">The `COR_TYPEID` structure is returned by a number of debugging methods that provide information about objects to be garbage-collected.</span></span> <span data-ttu-id="8b4d4-112">Může pak být předán jako argument jiné ladění metody, které poskytují další informace o této položce.</span><span class="sxs-lookup"><span data-stu-id="8b4d4-112">It can then be passed as an argument to other debugging methods that provide additional information about that item.</span></span> <span data-ttu-id="8b4d4-113">Například vytyčením [icordebugheapenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) objektu, je možné získat jednotlivé [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objekty, které představují jednotlivé objekty na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="8b4d4-113">For example, by enumerating an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) object, you can retrieve individual [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects that represent individual objects on the managed heap.</span></span> <span data-ttu-id="8b4d4-114">Můžete předat `COR_TYPEID` hodnotu `COR_HEAPOBJECT.type` pole [icordebugprocess5::gettypefortypeid –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) metodu pro načtení ICorDebugType objekt, který poskytuje typ informace o objektu.</span><span class="sxs-lookup"><span data-stu-id="8b4d4-114">You can then pass the `COR_TYPEID` value from the `COR_HEAPOBJECT.type` field to the [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) method to retrieve an ICorDebugType object that provides type information about the object.</span></span>  
  
 <span data-ttu-id="8b4d4-115">A `COR_TYPEID` objektu má být neprůhledné.</span><span class="sxs-lookup"><span data-stu-id="8b4d4-115">A `COR_TYPEID` object is intended to be opaque.</span></span> <span data-ttu-id="8b4d4-116">Jednotlivých polí by neměl být přistupovat ani s nimi manipulovat.</span><span class="sxs-lookup"><span data-stu-id="8b4d4-116">Its individual fields should not be accessed or manipulated.</span></span> <span data-ttu-id="8b4d4-117">Jako identifikátor, který je k dispozici jako je výhradní použití `out` parametr ve volání metody a, který může být předán do jiné metody, které poskytují další informace.</span><span class="sxs-lookup"><span data-stu-id="8b4d4-117">Its sole use is as an identifier that is provided as an `out` parameter in a method call and that can, in turn, be passed to other methods to provide additional information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b4d4-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8b4d4-118">Requirements</span></span>  
 <span data-ttu-id="8b4d4-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b4d4-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b4d4-120">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b4d4-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b4d4-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b4d4-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b4d4-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b4d4-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b4d4-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b4d4-123">See also</span></span>

- [<span data-ttu-id="8b4d4-124">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="8b4d4-124">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="8b4d4-125">Ladění</span><span class="sxs-lookup"><span data-stu-id="8b4d4-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
