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
ms.openlocfilehash: b88a7b0672e15097c60afbe069ce5b78bd5c38d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408137"
---
# <a name="cortypelayout-structure"></a><span data-ttu-id="8c991-102">COR_TYPE_LAYOUT – struktura</span><span class="sxs-lookup"><span data-stu-id="8c991-102">COR_TYPE_LAYOUT Structure</span></span>
<span data-ttu-id="8c991-103">Poskytuje informace o rozložení objektu v paměti.</span><span class="sxs-lookup"><span data-stu-id="8c991-103">Provides information about the layout of an object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c991-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c991-104">Syntax</span></span>  
  
```  
typedef struct COR_TYPE_LAYOUT {  
    COR_TYPEID parentID;  
    ULONG32 objectSize;  
    ULONG32 numFields;  
    ULONG32 boxOffset;  
    CorElementType type;  
} COR_TYPE_LAYOUT;  
```  
  
## <a name="members"></a><span data-ttu-id="8c991-105">Členové</span><span class="sxs-lookup"><span data-stu-id="8c991-105">Members</span></span>  
  
|<span data-ttu-id="8c991-106">Člen</span><span class="sxs-lookup"><span data-stu-id="8c991-106">Member</span></span>|<span data-ttu-id="8c991-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8c991-107">Description</span></span>|  
|------------|-----------------|  
|`parentID`|<span data-ttu-id="8c991-108">Identifikátor nadřazený typ pro tento typ.</span><span class="sxs-lookup"><span data-stu-id="8c991-108">The identifier of the parent type to this type.</span></span> <span data-ttu-id="8c991-109">Toto bude s id typu NULL (token1 = 0, token2 = 0) Pokud id typu odpovídá <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8c991-109">This will be the NULL type id (token1= 0, token2 = 0) if the type id corresponds to <xref:System.Object?displayProperty=nameWithType>.</span></span>|  
|`objectSize`|<span data-ttu-id="8c991-110">Základní velikost objektu tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="8c991-110">The base size of an object of this type.</span></span> <span data-ttu-id="8c991-111">Toto je celková velikost pro jiný proměnnou velikostí objekty.</span><span class="sxs-lookup"><span data-stu-id="8c991-111">This is the total size for non-variable sized objects.</span></span>|  
|`numFields`|<span data-ttu-id="8c991-112">Počet polí součástí objekty tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="8c991-112">The number of fields included in objects of this type.</span></span>|  
|`boxOffset`|<span data-ttu-id="8c991-113">Pokud je tento typ zabalená, počáteční posun objektu polí.</span><span class="sxs-lookup"><span data-stu-id="8c991-113">If this type is boxed, the beginning offset of an object's fields.</span></span> <span data-ttu-id="8c991-114">Toto pole je platná pouze pro typy hodnot, jako je například primitivních elementů a struktury.</span><span class="sxs-lookup"><span data-stu-id="8c991-114">This field is valid only for value types such as primitives and structures.</span></span>|  
|`type`|<span data-ttu-id="8c991-115">CorElementType, do které patří tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="8c991-115">The CorElementType to which this type belongs.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c991-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8c991-116">Remarks</span></span>  
 <span data-ttu-id="8c991-117">Pokud `numFields` je větší než nula, můžete zavolat [icordebugprocess5::gettypefields –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md) metodu za účelem získání informací o pole v tomto typu.</span><span class="sxs-lookup"><span data-stu-id="8c991-117">If `numFields` is greater than zero, you can call the [ICorDebugProcess5::GetTypeFields](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md) method to obtain information about the fields in this type.</span></span> <span data-ttu-id="8c991-118">Pokud `type` je `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, nebo `ELEMENT_TYPE_SZARRAY`, velikost objekty tohoto typu je proměnná a můžete předat [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) struktury k [icordebugprocess5::getarraylayout – ](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="8c991-118">If `type` is `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, or `ELEMENT_TYPE_SZARRAY`, the size of objects of this type is variable, and you can pass the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) structure to the [ICorDebugProcess5::GetArrayLayout](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c991-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8c991-119">Requirements</span></span>  
 <span data-ttu-id="8c991-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c991-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c991-121">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8c991-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c991-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c991-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c991-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c991-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c991-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="8c991-124">See Also</span></span>  
 [<span data-ttu-id="8c991-125">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="8c991-125">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="8c991-126">Ladění</span><span class="sxs-lookup"><span data-stu-id="8c991-126">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
