---
title: IDENTITY_ATTRIBUTE – struktura
ms.date: 03/30/2017
api_name:
- IDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDENTITY_ATTRIBUTE
helpviewer_keywords:
- IDENTITY_ATTRIBUTE structure [.NET Framework fusion]
ms.assetid: 1ee7c434-9681-4fa8-badd-652cb1a9742b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e0bcabb32d50b236d42a555c073b50ba3a234dde
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796484"
---
# <a name="identity_attribute-structure"></a><span data-ttu-id="70a42-102">IDENTITY_ATTRIBUTE – struktura</span><span class="sxs-lookup"><span data-stu-id="70a42-102">IDENTITY_ATTRIBUTE Structure</span></span>
<span data-ttu-id="70a42-103">Obsahuje informace o atributech metadat instance [IDefinitionIdentity –](idefinitionidentity-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="70a42-103">Contains metadata attribute information about an [IDefinitionIdentity](idefinitionidentity-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70a42-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70a42-104">Syntax</span></span>  
  
```cpp  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a><span data-ttu-id="70a42-105">Členové</span><span class="sxs-lookup"><span data-stu-id="70a42-105">Members</span></span>  
  
|<span data-ttu-id="70a42-106">Člen</span><span class="sxs-lookup"><span data-stu-id="70a42-106">Member</span></span>|<span data-ttu-id="70a42-107">Popis</span><span class="sxs-lookup"><span data-stu-id="70a42-107">Description</span></span>|  
|------------|-----------------|  
|`pszNamespace`|<span data-ttu-id="70a42-108">Ukazatel na řetězec znaků zakončený hodnotou null, který obsahuje obor názvů, ve kterém je atribut.</span><span class="sxs-lookup"><span data-stu-id="70a42-108">A pointer to a null-terminated character string that contains the namespace the attribute is in.</span></span>|  
|`pszName`|<span data-ttu-id="70a42-109">Ukazatel na řetězec znaků zakončený hodnotou null, který obsahuje název atributu.</span><span class="sxs-lookup"><span data-stu-id="70a42-109">A pointer to a null-terminated character string that contains the name of the attribute.</span></span>|  
|`pszValue`|<span data-ttu-id="70a42-110">Ukazatel na řetězec znaků zakončený hodnotou null, který obsahuje hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="70a42-110">A pointer to a null-terminated character string that contains the value of the attribute.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70a42-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="70a42-111">Remarks</span></span>  
 <span data-ttu-id="70a42-112">`IDENTITY_ATTRIBUTE` Struktura obsahuje tři ukazatele na řetězce znaků zakončených hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="70a42-112">The `IDENTITY_ATTRIBUTE` structure contains three pointers to null-terminated character strings.</span></span> <span data-ttu-id="70a42-113">Tyto tři řetězce popisují jeden atribut.</span><span class="sxs-lookup"><span data-stu-id="70a42-113">These three strings describe one attribute.</span></span>  
  
 <span data-ttu-id="70a42-114">Instance `IDENTITY_ATTRIBUTE` struktury je přidružená k instanci struktury [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="70a42-114">An instance of an `IDENTITY_ATTRIBUTE` structure is associated with an instance of an [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) structure.</span></span> <span data-ttu-id="70a42-115">Struktura obsahuje skutečné řetězce a odpovídající `IDENTITY_ATTRIBUTE_BLOB` struktura obsahuje seznam posunů ke `IDENTITY_ATTRIBUTE` třem řetězcům uvedeným ve struktuře. `IDENTITY_ATTRIBUTE`</span><span class="sxs-lookup"><span data-stu-id="70a42-115">The `IDENTITY_ATTRIBUTE` structure contains the actual strings, and the corresponding `IDENTITY_ATTRIBUTE_BLOB` structure lists the offsets to the three strings listed in the `IDENTITY_ATTRIBUTE` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70a42-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="70a42-116">Requirements</span></span>  
 <span data-ttu-id="70a42-117">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70a42-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70a42-118">**Hlaviček** Izolace. h</span><span class="sxs-lookup"><span data-stu-id="70a42-118">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="70a42-119">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70a42-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70a42-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70a42-120">See also</span></span>

- [<span data-ttu-id="70a42-121">IDefinitionIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="70a42-121">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)
- [<span data-ttu-id="70a42-122">IDENTITY_ATTRIBUTE_BLOB – struktura</span><span class="sxs-lookup"><span data-stu-id="70a42-122">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>](identity-attribute-blob-structure.md)
- [<span data-ttu-id="70a42-123">Struktury pro fúze</span><span class="sxs-lookup"><span data-stu-id="70a42-123">Fusion Structures</span></span>](fusion-structures.md)
