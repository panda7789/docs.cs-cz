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
ms.openlocfilehash: 80623bdec939b0ae5fc13008c1c4001c613ac435
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195961"
---
# <a name="bucketparameters-structure"></a><span data-ttu-id="aee2c-102">BucketParameters – struktura</span><span class="sxs-lookup"><span data-stu-id="aee2c-102">BucketParameters Structure</span></span>
<span data-ttu-id="aee2c-103">Ukládá název typu události a parametry pro aktuální výjimku, která je přidružena k události.</span><span class="sxs-lookup"><span data-stu-id="aee2c-103">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aee2c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aee2c-104">Syntax</span></span>  
  
```cpp  
typedef struct _BucketParameters {  
    BOOL  fInited;                    
    WCHAR pszEventTypeName[255];      
    WCHAR pszParams[10][255];         
} BucketParameters;  
```  
  
## <a name="members"></a><span data-ttu-id="aee2c-105">Členové</span><span class="sxs-lookup"><span data-stu-id="aee2c-105">Members</span></span>  
  
|<span data-ttu-id="aee2c-106">Člen</span><span class="sxs-lookup"><span data-stu-id="aee2c-106">Member</span></span>|<span data-ttu-id="aee2c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="aee2c-107">Description</span></span>|  
|------------|-----------------|  
|`fInited`|<span data-ttu-id="aee2c-108">`true`, pokud je zbytek této struktury platný; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="aee2c-108">`true`, if the rest of this structure is valid; otherwise, `false`.</span></span>|  
|`pszEventTypeName`|<span data-ttu-id="aee2c-109">Název typu události</span><span class="sxs-lookup"><span data-stu-id="aee2c-109">Name of the event type.</span></span>|  
|`pszParams`|<span data-ttu-id="aee2c-110">Pole řetězců, z nichž každý určuje parametr pro aktuální výjimku přidruženou k události.</span><span class="sxs-lookup"><span data-stu-id="aee2c-110">An array of strings, each of which specifies a parameter for the current exception associated with the event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aee2c-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aee2c-111">Requirements</span></span>  
 <span data-ttu-id="aee2c-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aee2c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aee2c-113">**Hlavička:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="aee2c-113">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="aee2c-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aee2c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aee2c-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aee2c-115">See also</span></span>

- [<span data-ttu-id="aee2c-116">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="aee2c-116">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
