---
title: COR_TYPE_LAYOUT – struktura
ms.date: 03/30/2017
api_name:
- COR_TYPE_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPE_LAYOUT
helpviewer_keywords:
- COR_TYPE_LAYOUT structure [.NET Framework debugging]
ms.assetid: 43a7addd-f25a-4049-9907-abec3eb17af2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bd274b1eb14532629580e777288317186544912
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274167"
---
# <a name="cor_type_layout-structure"></a><span data-ttu-id="15a6c-102">COR_TYPE_LAYOUT – struktura</span><span class="sxs-lookup"><span data-stu-id="15a6c-102">COR_TYPE_LAYOUT Structure</span></span>
<span data-ttu-id="15a6c-103">Poskytuje informace o rozložení objektu v paměti.</span><span class="sxs-lookup"><span data-stu-id="15a6c-103">Provides information about the layout of an object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15a6c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15a6c-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_TYPE_LAYOUT {  
    COR_TYPEID parentID;  
    ULONG32 objectSize;  
    ULONG32 numFields;  
    ULONG32 boxOffset;  
    CorElementType type;  
} COR_TYPE_LAYOUT;  
```  
  
## <a name="members"></a><span data-ttu-id="15a6c-105">Členové</span><span class="sxs-lookup"><span data-stu-id="15a6c-105">Members</span></span>  
  
|<span data-ttu-id="15a6c-106">Člen</span><span class="sxs-lookup"><span data-stu-id="15a6c-106">Member</span></span>|<span data-ttu-id="15a6c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="15a6c-107">Description</span></span>|  
|------------|-----------------|  
|`parentID`|<span data-ttu-id="15a6c-108">Identifikátor nadřazeného typu na tento typ.</span><span class="sxs-lookup"><span data-stu-id="15a6c-108">The identifier of the parent type to this type.</span></span> <span data-ttu-id="15a6c-109">Toto bude identifikátor typu s hodnotou NULL (token1 = 0, token2 = 0), pokud ID typu odpovídá <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="15a6c-109">This will be the NULL type id (token1= 0, token2 = 0) if the type id corresponds to <xref:System.Object?displayProperty=nameWithType>.</span></span>|  
|`objectSize`|<span data-ttu-id="15a6c-110">Základní velikost objektu tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="15a6c-110">The base size of an object of this type.</span></span> <span data-ttu-id="15a6c-111">Toto je celková velikost pro objekty, které nejsou proměnné velikosti.</span><span class="sxs-lookup"><span data-stu-id="15a6c-111">This is the total size for non-variable sized objects.</span></span>|  
|`numFields`|<span data-ttu-id="15a6c-112">Počet polí, která jsou součástí objektů tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="15a6c-112">The number of fields included in objects of this type.</span></span>|  
|`boxOffset`|<span data-ttu-id="15a6c-113">Pokud je tento typ zabalený, počáteční posun pole objektu.</span><span class="sxs-lookup"><span data-stu-id="15a6c-113">If this type is boxed, the beginning offset of an object's fields.</span></span> <span data-ttu-id="15a6c-114">Toto pole je platné pouze pro typy hodnot, jako jsou primitivní prvky a struktury.</span><span class="sxs-lookup"><span data-stu-id="15a6c-114">This field is valid only for value types such as primitives and structures.</span></span>|  
|`type`|<span data-ttu-id="15a6c-115">CorElementType –, ke kterému patří tento typ.</span><span class="sxs-lookup"><span data-stu-id="15a6c-115">The CorElementType to which this type belongs.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15a6c-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="15a6c-116">Remarks</span></span>  
 <span data-ttu-id="15a6c-117">Pokud `numFields` je větší než nula, můžete zavolat metodu [ICorDebugProcess5:: GetTypeFields –](icordebugprocess5-gettypefields-method.md) a získat informace o polích v tomto typu.</span><span class="sxs-lookup"><span data-stu-id="15a6c-117">If `numFields` is greater than zero, you can call the [ICorDebugProcess5::GetTypeFields](icordebugprocess5-gettypefields-method.md) method to obtain information about the fields in this type.</span></span> <span data-ttu-id="15a6c-118">Pokud `type` je `ELEMENT_TYPE_STRING` ,`ELEMENT_TYPE_ARRAY` [](cor-typeid-structure.md) nebo ,`ELEMENT_TYPE_SZARRAY`velikost objektů tohoto typu je proměnná, a můžete předat strukturu COR_TYPEID do metody [ICorDebugProcess5:: GetArrayLayout –](icordebugprocess5-getarraylayout-method.md) .</span><span class="sxs-lookup"><span data-stu-id="15a6c-118">If `type` is `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, or `ELEMENT_TYPE_SZARRAY`, the size of objects of this type is variable, and you can pass the [COR_TYPEID](cor-typeid-structure.md) structure to the [ICorDebugProcess5::GetArrayLayout](icordebugprocess5-getarraylayout-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15a6c-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="15a6c-119">Requirements</span></span>  
 <span data-ttu-id="15a6c-120">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15a6c-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15a6c-121">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="15a6c-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="15a6c-122">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15a6c-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15a6c-123">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15a6c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15a6c-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15a6c-124">See also</span></span>

- [<span data-ttu-id="15a6c-125">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="15a6c-125">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="15a6c-126">Ladění</span><span class="sxs-lookup"><span data-stu-id="15a6c-126">Debugging</span></span>](index.md)
