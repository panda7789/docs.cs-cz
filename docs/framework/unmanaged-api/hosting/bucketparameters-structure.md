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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5998ce684726b2386d8f1e05eb7eaeccf455747c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110453"
---
# <a name="bucketparameters-structure"></a><span data-ttu-id="1a9db-102">BucketParameters – struktura</span><span class="sxs-lookup"><span data-stu-id="1a9db-102">BucketParameters Structure</span></span>
<span data-ttu-id="1a9db-103">Ukládá název typu události a parametry pro aktuální výjimky, které je přidruženo k události.</span><span class="sxs-lookup"><span data-stu-id="1a9db-103">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a9db-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a9db-104">Syntax</span></span>  
  
```  
typedef struct _BucketParameters {  
    BOOL  fInited;                    
    WCHAR pszEventTypeName[255];      
    WCHAR pszParams[10][255];         
} BucketParameters;  
```  
  
## <a name="members"></a><span data-ttu-id="1a9db-105">Členové</span><span class="sxs-lookup"><span data-stu-id="1a9db-105">Members</span></span>  
  
|<span data-ttu-id="1a9db-106">Člen</span><span class="sxs-lookup"><span data-stu-id="1a9db-106">Member</span></span>|<span data-ttu-id="1a9db-107">Popis</span><span class="sxs-lookup"><span data-stu-id="1a9db-107">Description</span></span>|  
|------------|-----------------|  
|`fInited`|`true`<span data-ttu-id="1a9db-108">, pokud zbytek tato struktura je platná. v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="1a9db-108">, if the rest of this structure is valid; otherwise, `false`.</span></span>|  
|`pszEventTypeName`|<span data-ttu-id="1a9db-109">Název typu události.</span><span class="sxs-lookup"><span data-stu-id="1a9db-109">Name of the event type.</span></span>|  
|`pszParams`|<span data-ttu-id="1a9db-110">Pole řetězců, z nichž každý určuje parametr pro aktuální výjimky přidružené k události.</span><span class="sxs-lookup"><span data-stu-id="1a9db-110">An array of strings, each of which specifies a parameter for the current exception associated with the event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1a9db-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1a9db-111">Requirements</span></span>  
 <span data-ttu-id="1a9db-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a9db-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a9db-113">**Záhlaví:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="1a9db-113">**Header:** MSCorEE.idl</span></span>  
  
 **<span data-ttu-id="1a9db-114">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="1a9db-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1a9db-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1a9db-115">See also</span></span>

- [<span data-ttu-id="1a9db-116">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="1a9db-116">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
