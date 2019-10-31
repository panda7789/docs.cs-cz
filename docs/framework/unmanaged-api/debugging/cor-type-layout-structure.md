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
ms.openlocfilehash: 12c594f157c803d5fc179e09a8ca6c0ef40f3f44
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099028"
---
# <a name="cor_type_layout-structure"></a><span data-ttu-id="ed680-102">COR_TYPE_LAYOUT – struktura</span><span class="sxs-lookup"><span data-stu-id="ed680-102">COR_TYPE_LAYOUT Structure</span></span>
<span data-ttu-id="ed680-103">Poskytuje informace o rozložení objektu v paměti.</span><span class="sxs-lookup"><span data-stu-id="ed680-103">Provides information about the layout of an object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed680-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed680-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_TYPE_LAYOUT {  
    COR_TYPEID parentID;  
    ULONG32 objectSize;  
    ULONG32 numFields;  
    ULONG32 boxOffset;  
    CorElementType type;  
} COR_TYPE_LAYOUT;  
```  
  
## <a name="members"></a><span data-ttu-id="ed680-105">Členové</span><span class="sxs-lookup"><span data-stu-id="ed680-105">Members</span></span>  
  
|<span data-ttu-id="ed680-106">Člen</span><span class="sxs-lookup"><span data-stu-id="ed680-106">Member</span></span>|<span data-ttu-id="ed680-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ed680-107">Description</span></span>|  
|------------|-----------------|  
|`parentID`|<span data-ttu-id="ed680-108">Identifikátor nadřazeného typu na tento typ.</span><span class="sxs-lookup"><span data-stu-id="ed680-108">The identifier of the parent type to this type.</span></span> <span data-ttu-id="ed680-109">Toto bude identifikátor typu NULL (token1 = 0, token2 = 0), pokud ID typu odpovídá <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ed680-109">This will be the NULL type id (token1= 0, token2 = 0) if the type id corresponds to <xref:System.Object?displayProperty=nameWithType>.</span></span>|  
|`objectSize`|<span data-ttu-id="ed680-110">Základní velikost objektu tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="ed680-110">The base size of an object of this type.</span></span> <span data-ttu-id="ed680-111">Toto je celková velikost pro objekty, které nejsou proměnné velikosti.</span><span class="sxs-lookup"><span data-stu-id="ed680-111">This is the total size for non-variable sized objects.</span></span>|  
|`numFields`|<span data-ttu-id="ed680-112">Počet polí, která jsou součástí objektů tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="ed680-112">The number of fields included in objects of this type.</span></span>|  
|`boxOffset`|<span data-ttu-id="ed680-113">Pokud je tento typ zabalený, počáteční posun pole objektu.</span><span class="sxs-lookup"><span data-stu-id="ed680-113">If this type is boxed, the beginning offset of an object's fields.</span></span> <span data-ttu-id="ed680-114">Toto pole je platné pouze pro typy hodnot, jako jsou primitivní prvky a struktury.</span><span class="sxs-lookup"><span data-stu-id="ed680-114">This field is valid only for value types such as primitives and structures.</span></span>|  
|`type`|<span data-ttu-id="ed680-115">CorElementType –, ke kterému patří tento typ.</span><span class="sxs-lookup"><span data-stu-id="ed680-115">The CorElementType to which this type belongs.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed680-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ed680-116">Remarks</span></span>  
 <span data-ttu-id="ed680-117">Pokud je `numFields` větší než nula, můžete zavolat metodu [ICorDebugProcess5:: GetTypeFields –](icordebugprocess5-gettypefields-method.md) a získat informace o polích v tomto typu.</span><span class="sxs-lookup"><span data-stu-id="ed680-117">If `numFields` is greater than zero, you can call the [ICorDebugProcess5::GetTypeFields](icordebugprocess5-gettypefields-method.md) method to obtain information about the fields in this type.</span></span> <span data-ttu-id="ed680-118">Pokud je `type` `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`nebo `ELEMENT_TYPE_SZARRAY`, velikost objektů tohoto typu je proměnná a můžete předat strukturu [COR_TYPEID](cor-typeid-structure.md) do metody [ICorDebugProcess5:: GetArrayLayout –](icordebugprocess5-getarraylayout-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ed680-118">If `type` is `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, or `ELEMENT_TYPE_SZARRAY`, the size of objects of this type is variable, and you can pass the [COR_TYPEID](cor-typeid-structure.md) structure to the [ICorDebugProcess5::GetArrayLayout](icordebugprocess5-getarraylayout-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed680-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ed680-119">Requirements</span></span>  
 <span data-ttu-id="ed680-120">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed680-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed680-121">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ed680-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ed680-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ed680-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed680-123">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed680-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed680-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ed680-124">See also</span></span>

- [<span data-ttu-id="ed680-125">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="ed680-125">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="ed680-126">Ladění</span><span class="sxs-lookup"><span data-stu-id="ed680-126">Debugging</span></span>](index.md)
