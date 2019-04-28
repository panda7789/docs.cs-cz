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
ms.openlocfilehash: cb970d31fb5158adc7dbcbb7cc0175cc91c83c8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698041"
---
# <a name="identityattribute-structure"></a><span data-ttu-id="27500-102">IDENTITY_ATTRIBUTE – struktura</span><span class="sxs-lookup"><span data-stu-id="27500-102">IDENTITY_ATTRIBUTE Structure</span></span>
<span data-ttu-id="27500-103">Obsahuje informace o atributu metadata o [idefinitionidentity –](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="27500-103">Contains metadata attribute information about an [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27500-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27500-104">Syntax</span></span>  
  
```  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a><span data-ttu-id="27500-105">Členové</span><span class="sxs-lookup"><span data-stu-id="27500-105">Members</span></span>  
  
|<span data-ttu-id="27500-106">Člen</span><span class="sxs-lookup"><span data-stu-id="27500-106">Member</span></span>|<span data-ttu-id="27500-107">Popis</span><span class="sxs-lookup"><span data-stu-id="27500-107">Description</span></span>|  
|------------|-----------------|  
|`pszNamespace`|<span data-ttu-id="27500-108">Ukazatel na řetězec znaků zakončené znakem null, který obsahuje obor názvů příslušný atribut nachází v.</span><span class="sxs-lookup"><span data-stu-id="27500-108">A pointer to a null-terminated character string that contains the namespace the attribute is in.</span></span>|  
|`pszName`|<span data-ttu-id="27500-109">Ukazatel na řetězec znaků zakončené znakem null, který obsahuje název atributu.</span><span class="sxs-lookup"><span data-stu-id="27500-109">A pointer to a null-terminated character string that contains the name of the attribute.</span></span>|  
|`pszValue`|<span data-ttu-id="27500-110">Ukazatel na řetězec znaků zakončené znakem null, který obsahuje hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="27500-110">A pointer to a null-terminated character string that contains the value of the attribute.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27500-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="27500-111">Remarks</span></span>  
 <span data-ttu-id="27500-112">`IDENTITY_ATTRIBUTE` Struktura obsahuje tři ukazatele na řetězce znaků zakončených znakem null.</span><span class="sxs-lookup"><span data-stu-id="27500-112">The `IDENTITY_ATTRIBUTE` structure contains three pointers to null-terminated character strings.</span></span> <span data-ttu-id="27500-113">Tyto tři řetězce popisu jeden atribut.</span><span class="sxs-lookup"><span data-stu-id="27500-113">These three strings describe one attribute.</span></span>  
  
 <span data-ttu-id="27500-114">Instance `IDENTITY_ATTRIBUTE` struktura je přidružený k instanci [identity_attribute_blob –](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="27500-114">An instance of an `IDENTITY_ATTRIBUTE` structure is associated with an instance of an [IDENTITY_ATTRIBUTE_BLOB](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) structure.</span></span> <span data-ttu-id="27500-115">`IDENTITY_ATTRIBUTE` Struktura obsahuje skutečné řetězce a odpovídající `IDENTITY_ATTRIBUTE_BLOB` struktura obsahuje seznam posunutí pro tři řetězce, uvedené v `IDENTITY_ATTRIBUTE` struktury.</span><span class="sxs-lookup"><span data-stu-id="27500-115">The `IDENTITY_ATTRIBUTE` structure contains the actual strings, and the corresponding `IDENTITY_ATTRIBUTE_BLOB` structure lists the offsets to the three strings listed in the `IDENTITY_ATTRIBUTE` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27500-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="27500-116">Requirements</span></span>  
 <span data-ttu-id="27500-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27500-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27500-118">**Záhlaví:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="27500-118">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="27500-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27500-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27500-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="27500-120">See also</span></span>

- [<span data-ttu-id="27500-121">IDefinitionIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="27500-121">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)
- [<span data-ttu-id="27500-122">IDENTITY_ATTRIBUTE_BLOB – struktura</span><span class="sxs-lookup"><span data-stu-id="27500-122">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)
- [<span data-ttu-id="27500-123">Struktury pro fúze</span><span class="sxs-lookup"><span data-stu-id="27500-123">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
