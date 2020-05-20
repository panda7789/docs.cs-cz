---
title: BucketParameters – struktura
ms.date: 03/30/2017
api_name:
- BucketParameters
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- BucketParameters
helpviewer_keywords:
- BucketParameters structure [.NET Framework hosting]
ms.assetid: 9432487e-f276-45d6-9a13-9a68024dbd46
topic_type:
- apiref
ms.openlocfilehash: 7037065be138c369b847e7f86de7b46fc5ae601a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616876"
---
# <a name="bucketparameters-structure"></a><span data-ttu-id="8ef58-102">BucketParameters – struktura</span><span class="sxs-lookup"><span data-stu-id="8ef58-102">BucketParameters Structure</span></span>
<span data-ttu-id="8ef58-103">Ukládá název typu události a parametry pro aktuální výjimku, která je přidružena k události.</span><span class="sxs-lookup"><span data-stu-id="8ef58-103">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ef58-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ef58-104">Syntax</span></span>  
  
```cpp  
typedef struct _BucketParameters {  
    BOOL  fInited;
    WCHAR pszEventTypeName[255];
    WCHAR pszParams[10][255];
} BucketParameters;  
```  
  
## <a name="members"></a><span data-ttu-id="8ef58-105">Členové</span><span class="sxs-lookup"><span data-stu-id="8ef58-105">Members</span></span>  
  
|<span data-ttu-id="8ef58-106">Člen</span><span class="sxs-lookup"><span data-stu-id="8ef58-106">Member</span></span>|<span data-ttu-id="8ef58-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8ef58-107">Description</span></span>|  
|------------|-----------------|  
|`fInited`|<span data-ttu-id="8ef58-108">`true`, pokud je zbytek této struktury platný; v opačném případě `false` .</span><span class="sxs-lookup"><span data-stu-id="8ef58-108">`true`, if the rest of this structure is valid; otherwise, `false`.</span></span>|  
|`pszEventTypeName`|<span data-ttu-id="8ef58-109">Název typu události</span><span class="sxs-lookup"><span data-stu-id="8ef58-109">Name of the event type.</span></span>|  
|`pszParams`|<span data-ttu-id="8ef58-110">Pole řetězců, z nichž každý určuje parametr pro aktuální výjimku přidruženou k události.</span><span class="sxs-lookup"><span data-stu-id="8ef58-110">An array of strings, each of which specifies a parameter for the current exception associated with the event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8ef58-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8ef58-111">Requirements</span></span>  
 <span data-ttu-id="8ef58-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ef58-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ef58-113">**Hlavička:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="8ef58-113">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="8ef58-114">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ef58-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ef58-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ef58-115">See also</span></span>

- [<span data-ttu-id="8ef58-116">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="8ef58-116">Hosting Structures</span></span>](hosting-structures.md)
