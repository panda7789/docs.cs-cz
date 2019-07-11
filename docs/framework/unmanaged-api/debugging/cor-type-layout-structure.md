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
ms.openlocfilehash: 1793547cfc0d9637352b62ff47beee41e9f5ac5c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740500"
---
# <a name="cortypelayout-structure"></a><span data-ttu-id="dfc18-102">COR_TYPE_LAYOUT – struktura</span><span class="sxs-lookup"><span data-stu-id="dfc18-102">COR_TYPE_LAYOUT Structure</span></span>
<span data-ttu-id="dfc18-103">Poskytuje informace o rozložení objektu v paměti.</span><span class="sxs-lookup"><span data-stu-id="dfc18-103">Provides information about the layout of an object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfc18-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dfc18-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_TYPE_LAYOUT {  
    COR_TYPEID parentID;  
    ULONG32 objectSize;  
    ULONG32 numFields;  
    ULONG32 boxOffset;  
    CorElementType type;  
} COR_TYPE_LAYOUT;  
```  
  
## <a name="members"></a><span data-ttu-id="dfc18-105">Členové</span><span class="sxs-lookup"><span data-stu-id="dfc18-105">Members</span></span>  
  
|<span data-ttu-id="dfc18-106">Člen</span><span class="sxs-lookup"><span data-stu-id="dfc18-106">Member</span></span>|<span data-ttu-id="dfc18-107">Popis</span><span class="sxs-lookup"><span data-stu-id="dfc18-107">Description</span></span>|  
|------------|-----------------|  
|`parentID`|<span data-ttu-id="dfc18-108">Identifikátor k tomuto typu nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="dfc18-108">The identifier of the parent type to this type.</span></span> <span data-ttu-id="dfc18-109">Bude jím typ id hodnotu NULL (token1 = 0, token2 = 0) Pokud id typu odpovídá <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dfc18-109">This will be the NULL type id (token1= 0, token2 = 0) if the type id corresponds to <xref:System.Object?displayProperty=nameWithType>.</span></span>|  
|`objectSize`|<span data-ttu-id="dfc18-110">Základní velikost objektu tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="dfc18-110">The base size of an object of this type.</span></span> <span data-ttu-id="dfc18-111">Toto je celková velikost velkých objektů bez proměnných.</span><span class="sxs-lookup"><span data-stu-id="dfc18-111">This is the total size for non-variable sized objects.</span></span>|  
|`numFields`|<span data-ttu-id="dfc18-112">Počet polí, které jsou součástí objekty tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="dfc18-112">The number of fields included in objects of this type.</span></span>|  
|`boxOffset`|<span data-ttu-id="dfc18-113">Pokud je tento typ v poli, počáteční posun objektu polí.</span><span class="sxs-lookup"><span data-stu-id="dfc18-113">If this type is boxed, the beginning offset of an object's fields.</span></span> <span data-ttu-id="dfc18-114">Toto pole je platný pouze pro typy hodnot, jako je například primitiv a struktury.</span><span class="sxs-lookup"><span data-stu-id="dfc18-114">This field is valid only for value types such as primitives and structures.</span></span>|  
|`type`|<span data-ttu-id="dfc18-115">Corelementtype –, do které tento typ patří.</span><span class="sxs-lookup"><span data-stu-id="dfc18-115">The CorElementType to which this type belongs.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dfc18-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dfc18-116">Remarks</span></span>  
 <span data-ttu-id="dfc18-117">Pokud `numFields` je větší než nula, můžete volat [icordebugprocess5::gettypefields –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md) metodu k získání informací o polích v tomto typu.</span><span class="sxs-lookup"><span data-stu-id="dfc18-117">If `numFields` is greater than zero, you can call the [ICorDebugProcess5::GetTypeFields](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md) method to obtain information about the fields in this type.</span></span> <span data-ttu-id="dfc18-118">Pokud `type` je `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, nebo `ELEMENT_TYPE_SZARRAY`velikost objekty tohoto typu je proměnná a můžete předat [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) struktury na [icordebugprocess5::getarraylayout – ](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="dfc18-118">If `type` is `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, or `ELEMENT_TYPE_SZARRAY`, the size of objects of this type is variable, and you can pass the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) structure to the [ICorDebugProcess5::GetArrayLayout](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfc18-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dfc18-119">Requirements</span></span>  
 <span data-ttu-id="dfc18-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfc18-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfc18-121">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dfc18-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dfc18-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dfc18-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dfc18-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfc18-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfc18-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dfc18-124">See also</span></span>

- [<span data-ttu-id="dfc18-125">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="dfc18-125">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="dfc18-126">Ladění</span><span class="sxs-lookup"><span data-stu-id="dfc18-126">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
