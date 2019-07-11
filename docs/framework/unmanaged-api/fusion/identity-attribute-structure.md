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
ms.openlocfilehash: de1646cdbc11369b43a821d8b762879d1df7ed2e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751532"
---
# <a name="identityattribute-structure"></a><span data-ttu-id="264d6-102">IDENTITY_ATTRIBUTE – struktura</span><span class="sxs-lookup"><span data-stu-id="264d6-102">IDENTITY_ATTRIBUTE Structure</span></span>
<span data-ttu-id="264d6-103">Obsahuje informace o atributu metadata o [idefinitionidentity –](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="264d6-103">Contains metadata attribute information about an [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="264d6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="264d6-104">Syntax</span></span>  
  
```cpp  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a><span data-ttu-id="264d6-105">Členové</span><span class="sxs-lookup"><span data-stu-id="264d6-105">Members</span></span>  
  
|<span data-ttu-id="264d6-106">Člen</span><span class="sxs-lookup"><span data-stu-id="264d6-106">Member</span></span>|<span data-ttu-id="264d6-107">Popis</span><span class="sxs-lookup"><span data-stu-id="264d6-107">Description</span></span>|  
|------------|-----------------|  
|`pszNamespace`|<span data-ttu-id="264d6-108">Ukazatel na řetězec znaků zakončené znakem null, který obsahuje obor názvů příslušný atribut nachází v.</span><span class="sxs-lookup"><span data-stu-id="264d6-108">A pointer to a null-terminated character string that contains the namespace the attribute is in.</span></span>|  
|`pszName`|<span data-ttu-id="264d6-109">Ukazatel na řetězec znaků zakončené znakem null, který obsahuje název atributu.</span><span class="sxs-lookup"><span data-stu-id="264d6-109">A pointer to a null-terminated character string that contains the name of the attribute.</span></span>|  
|`pszValue`|<span data-ttu-id="264d6-110">Ukazatel na řetězec znaků zakončené znakem null, který obsahuje hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="264d6-110">A pointer to a null-terminated character string that contains the value of the attribute.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="264d6-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="264d6-111">Remarks</span></span>  
 <span data-ttu-id="264d6-112">`IDENTITY_ATTRIBUTE` Struktura obsahuje tři ukazatele na řetězce znaků zakončených znakem null.</span><span class="sxs-lookup"><span data-stu-id="264d6-112">The `IDENTITY_ATTRIBUTE` structure contains three pointers to null-terminated character strings.</span></span> <span data-ttu-id="264d6-113">Tyto tři řetězce popisu jeden atribut.</span><span class="sxs-lookup"><span data-stu-id="264d6-113">These three strings describe one attribute.</span></span>  
  
 <span data-ttu-id="264d6-114">Instance `IDENTITY_ATTRIBUTE` struktura je přidružený k instanci [identity_attribute_blob –](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="264d6-114">An instance of an `IDENTITY_ATTRIBUTE` structure is associated with an instance of an [IDENTITY_ATTRIBUTE_BLOB](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) structure.</span></span> <span data-ttu-id="264d6-115">`IDENTITY_ATTRIBUTE` Struktura obsahuje skutečné řetězce a odpovídající `IDENTITY_ATTRIBUTE_BLOB` struktura obsahuje seznam posunutí pro tři řetězce, uvedené v `IDENTITY_ATTRIBUTE` struktury.</span><span class="sxs-lookup"><span data-stu-id="264d6-115">The `IDENTITY_ATTRIBUTE` structure contains the actual strings, and the corresponding `IDENTITY_ATTRIBUTE_BLOB` structure lists the offsets to the three strings listed in the `IDENTITY_ATTRIBUTE` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="264d6-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="264d6-116">Requirements</span></span>  
 <span data-ttu-id="264d6-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="264d6-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="264d6-118">**Záhlaví:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="264d6-118">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="264d6-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="264d6-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="264d6-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="264d6-120">See also</span></span>

- [<span data-ttu-id="264d6-121">IDefinitionIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="264d6-121">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)
- [<span data-ttu-id="264d6-122">IDENTITY_ATTRIBUTE_BLOB – struktura</span><span class="sxs-lookup"><span data-stu-id="264d6-122">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)
- [<span data-ttu-id="264d6-123">Struktury pro fúze</span><span class="sxs-lookup"><span data-stu-id="264d6-123">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
