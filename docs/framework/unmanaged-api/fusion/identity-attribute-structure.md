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
ms.openlocfilehash: 8b7edf1cc642228c4a79c855b51727264f31741c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107983"
---
# <a name="identity_attribute-structure"></a><span data-ttu-id="197b9-102">IDENTITY_ATTRIBUTE – struktura</span><span class="sxs-lookup"><span data-stu-id="197b9-102">IDENTITY_ATTRIBUTE Structure</span></span>
<span data-ttu-id="197b9-103">Obsahuje informace o atributech metadat instance [IDefinitionIdentity –](idefinitionidentity-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="197b9-103">Contains metadata attribute information about an [IDefinitionIdentity](idefinitionidentity-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="197b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="197b9-104">Syntax</span></span>  
  
```cpp  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a><span data-ttu-id="197b9-105">Členové</span><span class="sxs-lookup"><span data-stu-id="197b9-105">Members</span></span>  
  
|<span data-ttu-id="197b9-106">Člen</span><span class="sxs-lookup"><span data-stu-id="197b9-106">Member</span></span>|<span data-ttu-id="197b9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="197b9-107">Description</span></span>|  
|------------|-----------------|  
|`pszNamespace`|<span data-ttu-id="197b9-108">Ukazatel na řetězec znaků zakončený hodnotou null, který obsahuje obor názvů, ve kterém je atribut.</span><span class="sxs-lookup"><span data-stu-id="197b9-108">A pointer to a null-terminated character string that contains the namespace the attribute is in.</span></span>|  
|`pszName`|<span data-ttu-id="197b9-109">Ukazatel na řetězec znaků zakončený hodnotou null, který obsahuje název atributu.</span><span class="sxs-lookup"><span data-stu-id="197b9-109">A pointer to a null-terminated character string that contains the name of the attribute.</span></span>|  
|`pszValue`|<span data-ttu-id="197b9-110">Ukazatel na řetězec znaků zakončený hodnotou null, který obsahuje hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="197b9-110">A pointer to a null-terminated character string that contains the value of the attribute.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="197b9-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="197b9-111">Remarks</span></span>  
 <span data-ttu-id="197b9-112">Struktura `IDENTITY_ATTRIBUTE` obsahuje tři ukazatele na řetězce znaků zakončených hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="197b9-112">The `IDENTITY_ATTRIBUTE` structure contains three pointers to null-terminated character strings.</span></span> <span data-ttu-id="197b9-113">Tyto tři řetězce popisují jeden atribut.</span><span class="sxs-lookup"><span data-stu-id="197b9-113">These three strings describe one attribute.</span></span>  
  
 <span data-ttu-id="197b9-114">Instance struktury `IDENTITY_ATTRIBUTE` je přidružená k instanci struktury [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="197b9-114">An instance of an `IDENTITY_ATTRIBUTE` structure is associated with an instance of an [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) structure.</span></span> <span data-ttu-id="197b9-115">Struktura `IDENTITY_ATTRIBUTE` obsahuje skutečné řetězce a odpovídající `IDENTITY_ATTRIBUTE_BLOB` struktura vypisuje posuny k třem řetězcům uvedeným ve struktuře `IDENTITY_ATTRIBUTE`.</span><span class="sxs-lookup"><span data-stu-id="197b9-115">The `IDENTITY_ATTRIBUTE` structure contains the actual strings, and the corresponding `IDENTITY_ATTRIBUTE_BLOB` structure lists the offsets to the three strings listed in the `IDENTITY_ATTRIBUTE` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="197b9-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="197b9-116">Requirements</span></span>  
 <span data-ttu-id="197b9-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="197b9-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="197b9-118">**Hlavička:** Izolace. h</span><span class="sxs-lookup"><span data-stu-id="197b9-118">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="197b9-119">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="197b9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="197b9-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="197b9-120">See also</span></span>

- [<span data-ttu-id="197b9-121">IDefinitionIdentity – rozhraní</span><span class="sxs-lookup"><span data-stu-id="197b9-121">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)
- [<span data-ttu-id="197b9-122">IDENTITY_ATTRIBUTE_BLOB – struktura</span><span class="sxs-lookup"><span data-stu-id="197b9-122">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>](identity-attribute-blob-structure.md)
- [<span data-ttu-id="197b9-123">Struktury pro fúze</span><span class="sxs-lookup"><span data-stu-id="197b9-123">Fusion Structures</span></span>](fusion-structures.md)
