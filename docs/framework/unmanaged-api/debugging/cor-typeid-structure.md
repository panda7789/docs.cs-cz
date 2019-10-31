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
ms.openlocfilehash: 4f6dbe8c17bd6a91078b87a87c1055fbf4977a88
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132298"
---
# <a name="cor_typeid-structure"></a><span data-ttu-id="45def-102">COR_TYPEID – struktura</span><span class="sxs-lookup"><span data-stu-id="45def-102">COR_TYPEID Structure</span></span>
<span data-ttu-id="45def-103">Obsahuje identifikátor typu.</span><span class="sxs-lookup"><span data-stu-id="45def-103">Contains a type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45def-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45def-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a><span data-ttu-id="45def-105">Členové</span><span class="sxs-lookup"><span data-stu-id="45def-105">Members</span></span>  
  
|<span data-ttu-id="45def-106">Člen</span><span class="sxs-lookup"><span data-stu-id="45def-106">Member</span></span>|<span data-ttu-id="45def-107">Popis</span><span class="sxs-lookup"><span data-stu-id="45def-107">Description</span></span>|  
|------------|-----------------|  
|`token1`|<span data-ttu-id="45def-108">První token.</span><span class="sxs-lookup"><span data-stu-id="45def-108">The first token.</span></span>|  
|`token2`|<span data-ttu-id="45def-109">Druhý token.</span><span class="sxs-lookup"><span data-stu-id="45def-109">The second token.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45def-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="45def-110">Remarks</span></span>  
 <span data-ttu-id="45def-111">Struktura `COR_TYPEID` je vrácena několika metodami ladění, které poskytují informace o objektech, které mají být sbírány do paměti.</span><span class="sxs-lookup"><span data-stu-id="45def-111">The `COR_TYPEID` structure is returned by a number of debugging methods that provide information about objects to be garbage-collected.</span></span> <span data-ttu-id="45def-112">Lze jej předat jako argument pro jiné metody ladění, které poskytují další informace o této položce.</span><span class="sxs-lookup"><span data-stu-id="45def-112">It can then be passed as an argument to other debugging methods that provide additional information about that item.</span></span> <span data-ttu-id="45def-113">Například vytvořením výčtu objektu [ICorDebugHeapEnum –](icordebugheapenum-interface.md) můžete načíst jednotlivé objekty [COR_HEAPOBJECT](cor-heapobject-structure.md) , které reprezentují jednotlivé objekty ve spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="45def-113">For example, by enumerating an [ICorDebugHeapEnum](icordebugheapenum-interface.md) object, you can retrieve individual [COR_HEAPOBJECT](cor-heapobject-structure.md) objects that represent individual objects on the managed heap.</span></span> <span data-ttu-id="45def-114">Pak můžete předat `COR_TYPEID` hodnotu z pole `COR_HEAPOBJECT.type` do metody [ICorDebugProcess5:: GetTypeForTypeID –](icordebugprocess5-gettypefortypeid-method.md) pro načtení objektu ICorDebugType, který poskytuje informace o typu objektu.</span><span class="sxs-lookup"><span data-stu-id="45def-114">You can then pass the `COR_TYPEID` value from the `COR_HEAPOBJECT.type` field to the [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) method to retrieve an ICorDebugType object that provides type information about the object.</span></span>  
  
 <span data-ttu-id="45def-115">Objekt `COR_TYPEID` má být neprůhledný.</span><span class="sxs-lookup"><span data-stu-id="45def-115">A `COR_TYPEID` object is intended to be opaque.</span></span> <span data-ttu-id="45def-116">K jednotlivým polím by neměl být přistup nebo manipulace.</span><span class="sxs-lookup"><span data-stu-id="45def-116">Its individual fields should not be accessed or manipulated.</span></span> <span data-ttu-id="45def-117">Jeho jediným použitím je identifikátor, který je k dispozici jako parametr `out` ve volání metody a který může být následně předán jiným metodám k poskytnutí dalších informací.</span><span class="sxs-lookup"><span data-stu-id="45def-117">Its sole use is as an identifier that is provided as an `out` parameter in a method call and that can, in turn, be passed to other methods to provide additional information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45def-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="45def-118">Requirements</span></span>  
 <span data-ttu-id="45def-119">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45def-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45def-120">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="45def-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45def-121">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="45def-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45def-122">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45def-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45def-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="45def-123">See also</span></span>

- [<span data-ttu-id="45def-124">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="45def-124">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="45def-125">Ladění</span><span class="sxs-lookup"><span data-stu-id="45def-125">Debugging</span></span>](index.md)
