---
title: "BucketParameters – struktura"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9db30133a01877c6ae048b9152f35b066219aa22
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="bucketparameters-structure"></a><span data-ttu-id="7030e-102">BucketParameters – struktura</span><span class="sxs-lookup"><span data-stu-id="7030e-102">BucketParameters Structure</span></span>
<span data-ttu-id="7030e-103">Ukládá název typu události a parametry pro aktuální výjimka, ke které je přidruženo k události.</span><span class="sxs-lookup"><span data-stu-id="7030e-103">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7030e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7030e-104">Syntax</span></span>  
  
```  
typedef struct _BucketParameters {  
    BOOL  fInited;                    
    WCHAR pszEventTypeName[255];      
    WCHAR pszParams[10][255];         
} BucketParameters;  
```  
  
## <a name="members"></a><span data-ttu-id="7030e-105">Členové</span><span class="sxs-lookup"><span data-stu-id="7030e-105">Members</span></span>  
  
|<span data-ttu-id="7030e-106">Člen</span><span class="sxs-lookup"><span data-stu-id="7030e-106">Member</span></span>|<span data-ttu-id="7030e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7030e-107">Description</span></span>|  
|------------|-----------------|  
|`fInited`|<span data-ttu-id="7030e-108">`true`, pokud je platná; zbytek tato struktura v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="7030e-108">`true`, if the rest of this structure is valid; otherwise, `false`.</span></span>|  
|`pszEventTypeName`|<span data-ttu-id="7030e-109">Název typu události.</span><span class="sxs-lookup"><span data-stu-id="7030e-109">Name of the event type.</span></span>|  
|`pszParams`|<span data-ttu-id="7030e-110">Pole řetězců, z nichž každý určuje parametr pro aktuální výjimky přidružený k události.</span><span class="sxs-lookup"><span data-stu-id="7030e-110">An array of strings, each of which specifies a parameter for the current exception associated with the event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7030e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7030e-111">Requirements</span></span>  
 <span data-ttu-id="7030e-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7030e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7030e-113">**Záhlaví:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="7030e-113">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="7030e-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7030e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7030e-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="7030e-115">See Also</span></span>  
 [<span data-ttu-id="7030e-116">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="7030e-116">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
