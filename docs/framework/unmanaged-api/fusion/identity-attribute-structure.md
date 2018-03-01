---
title: "IDENTITY_ATTRIBUTE – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2c0d09bf4c24f977a490f946cbc35b2b3f53dfc3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="identityattribute-structure"></a><span data-ttu-id="74632-102">IDENTITY_ATTRIBUTE – struktura</span><span class="sxs-lookup"><span data-stu-id="74632-102">IDENTITY_ATTRIBUTE Structure</span></span>
<span data-ttu-id="74632-103">Obsahuje informace o atributu metadata o [idefinitionidentity –](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="74632-103">Contains metadata attribute information about an [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74632-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74632-104">Syntax</span></span>  
  
```  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a><span data-ttu-id="74632-105">Členové</span><span class="sxs-lookup"><span data-stu-id="74632-105">Members</span></span>  
  
|<span data-ttu-id="74632-106">Člen</span><span class="sxs-lookup"><span data-stu-id="74632-106">Member</span></span>|<span data-ttu-id="74632-107">Popis</span><span class="sxs-lookup"><span data-stu-id="74632-107">Description</span></span>|  
|------------|-----------------|  
|`pszNamespace`|<span data-ttu-id="74632-108">Ukazatel na řetězec znaků ukončené hodnotou null, která obsahuje obor názvů je atribut v.</span><span class="sxs-lookup"><span data-stu-id="74632-108">A pointer to a null-terminated character string that contains the namespace the attribute is in.</span></span>|  
|`pszName`|<span data-ttu-id="74632-109">Ukazatel na řetězec znaků ukončené hodnotou null, který obsahuje název atributu.</span><span class="sxs-lookup"><span data-stu-id="74632-109">A pointer to a null-terminated character string that contains the name of the attribute.</span></span>|  
|`pszValue`|<span data-ttu-id="74632-110">Ukazatel na řetězec znaků ukončený hodnotou null, obsahující hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="74632-110">A pointer to a null-terminated character string that contains the value of the attribute.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74632-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74632-111">Remarks</span></span>  
 <span data-ttu-id="74632-112">`IDENTITY_ATTRIBUTE` Struktura obsahuje tři ukazatele na řetězce ukončené hodnotou null znaků.</span><span class="sxs-lookup"><span data-stu-id="74632-112">The `IDENTITY_ATTRIBUTE` structure contains three pointers to null-terminated character strings.</span></span> <span data-ttu-id="74632-113">Tyto tři řetězce popisují jeden atribut.</span><span class="sxs-lookup"><span data-stu-id="74632-113">These three strings describe one attribute.</span></span>  
  
 <span data-ttu-id="74632-114">Instance `IDENTITY_ATTRIBUTE` struktura je přidružený instanci [identity_attribute_blob –](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) struktura.</span><span class="sxs-lookup"><span data-stu-id="74632-114">An instance of an `IDENTITY_ATTRIBUTE` structure is associated with an instance of an [IDENTITY_ATTRIBUTE_BLOB](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) structure.</span></span> <span data-ttu-id="74632-115">`IDENTITY_ATTRIBUTE` Struktura obsahuje skutečné řetězce a odpovídající `IDENTITY_ATTRIBUTE_BLOB` struktura uvádí posunutí na tři řetězce uvedené v `IDENTITY_ATTRIBUTE` struktura.</span><span class="sxs-lookup"><span data-stu-id="74632-115">The `IDENTITY_ATTRIBUTE` structure contains the actual strings, and the corresponding `IDENTITY_ATTRIBUTE_BLOB` structure lists the offsets to the three strings listed in the `IDENTITY_ATTRIBUTE` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74632-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="74632-116">Requirements</span></span>  
 <span data-ttu-id="74632-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74632-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74632-118">**Záhlaví:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="74632-118">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="74632-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74632-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74632-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="74632-120">See Also</span></span>  
 [<span data-ttu-id="74632-121">IDefinitionIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74632-121">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)  
 [<span data-ttu-id="74632-122">IDENTITY_ATTRIBUTE_BLOB – struktura</span><span class="sxs-lookup"><span data-stu-id="74632-122">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)  
 [<span data-ttu-id="74632-123">Struktury pro fúze</span><span class="sxs-lookup"><span data-stu-id="74632-123">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
