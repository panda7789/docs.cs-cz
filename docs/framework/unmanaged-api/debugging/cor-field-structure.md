---
title: COR_FIELD – struktura
ms.date: 03/30/2017
api_name:
- COR_FIELD
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_FIELD
helpviewer_keywords:
- COR_FIELD structure [.NET Framework debugging]
ms.assetid: c0822423-a9df-4961-950d-50dcc152f863
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 691041632312bf8ac7c82a11724dcd725e14a420
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59231055"
---
# <a name="corfield-structure"></a><span data-ttu-id="b9b5e-102">COR_FIELD – struktura</span><span class="sxs-lookup"><span data-stu-id="b9b5e-102">COR_FIELD Structure</span></span>
<span data-ttu-id="b9b5e-103">Poskytuje informace o pole v objektu.</span><span class="sxs-lookup"><span data-stu-id="b9b5e-103">Provides information about a field in an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9b5e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9b5e-104">Syntax</span></span>  
  
```  
typedef struct COR_FIELD{  
    mdFieldDef token;  
    ULONG32 offset;  
    COR_TYPEID id;  
    CorElementType fieldType;  
} COR_FIELD;  
```  
  
## <a name="members"></a><span data-ttu-id="b9b5e-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b9b5e-105">Members</span></span>  
  
|<span data-ttu-id="b9b5e-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b9b5e-106">Member</span></span>|<span data-ttu-id="b9b5e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b9b5e-107">Description</span></span>|  
|------------|-----------------|  
|`token`|<span data-ttu-id="b9b5e-108">`mdFieldDef` Token, který můžete použít k získání informací o poli.</span><span class="sxs-lookup"><span data-stu-id="b9b5e-108">An `mdFieldDef` token that can be used to get field information.</span></span>|  
|`offset`|<span data-ttu-id="b9b5e-109">Posun v bajtech pro data polí v objektu.</span><span class="sxs-lookup"><span data-stu-id="b9b5e-109">The offset, in bytes, to the field data in the object.</span></span>|  
|`id`|<span data-ttu-id="b9b5e-110">A [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) hodnotu, která určuje typ tohoto pole.</span><span class="sxs-lookup"><span data-stu-id="b9b5e-110">A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) value that identifies the type of this field.</span></span>|  
|`fieldType`|<span data-ttu-id="b9b5e-111">Corelementtype – hodnotu výčtu, která určuje typ pole.</span><span class="sxs-lookup"><span data-stu-id="b9b5e-111">A CorElementType enumeration value that indicates the type of the field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9b5e-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b9b5e-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9b5e-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b9b5e-113">Requirements</span></span>  
 <span data-ttu-id="b9b5e-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9b5e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9b5e-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b9b5e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9b5e-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9b5e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9b5e-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9b5e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9b5e-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b9b5e-118">See also</span></span>

- [<span data-ttu-id="b9b5e-119">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="b9b5e-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="b9b5e-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="b9b5e-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
