---
title: "EContextType – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EContextType
api_location: mscoree.dll
api_type: COM
f1_keywords: EContextType
helpviewer_keywords: EContextType enumeration [.NET Framework hosting]
ms.assetid: 92b926a9-b87e-408a-9036-df7b752c9492
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 73e6e9a1f1118a524b86b3711c0c7a6af4777f2d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="econtexttype-enumeration"></a><span data-ttu-id="3f0af-102">EContextType – výčet</span><span class="sxs-lookup"><span data-stu-id="3f0af-102">EContextType Enumeration</span></span>
<span data-ttu-id="3f0af-103">Popisuje kontext zabezpečení aktuálně prováděné vlákno.</span><span class="sxs-lookup"><span data-stu-id="3f0af-103">Describes the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f0af-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f0af-104">Syntax</span></span>  
  
```  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a><span data-ttu-id="3f0af-105">Členové</span><span class="sxs-lookup"><span data-stu-id="3f0af-105">Members</span></span>  
  
|<span data-ttu-id="3f0af-106">Člen</span><span class="sxs-lookup"><span data-stu-id="3f0af-106">Member</span></span>|<span data-ttu-id="3f0af-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3f0af-107">Description</span></span>|  
|------------|-----------------|  
|`eCurrentContext`|<span data-ttu-id="3f0af-108">Určuje kontext na aktuální vlákno v okamžiku volá modul CLR (CLR) [ihostsecuritymanager::getsecuritycontext –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) metoda nebo kontext požadoval CLR v volání [ Ihostsecuritymanager::setsecuritycontext –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="3f0af-108">Indicates the context on the current thread at the time the common language runtime (CLR) calls the [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) method, or the context requested by the CLR in a call to the [IHostSecurityManager::SetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md) method.</span></span>|  
|`eRestrictedContext`|<span data-ttu-id="3f0af-109">Označuje kontextu, po kterou má hostitel nižší oprávnění, například systém uvolňování paměti nebo třídy nebo modulu konstruktory.</span><span class="sxs-lookup"><span data-stu-id="3f0af-109">Indicates a context over which the host has lower privileges, such as the garbage collector, or class or module constructors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f0af-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3f0af-110">Remarks</span></span>  
 <span data-ttu-id="3f0af-111">Modul CLR poskytuje jeden z `EContextType` hodnoty jako hodnotu parametru ve voláních `IHostSecurityManager::GetSecurityContext` a `IHostSecurityManager::SetSecurityContext` metody.</span><span class="sxs-lookup"><span data-stu-id="3f0af-111">The CLR supplies one of the `EContextType` values as a parameter value in calls to the `IHostSecurityManager::GetSecurityContext` and `IHostSecurityManager::SetSecurityContext` methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f0af-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3f0af-112">Requirements</span></span>  
 <span data-ttu-id="3f0af-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f0af-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f0af-114">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3f0af-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3f0af-115">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3f0af-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3f0af-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f0af-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f0af-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f0af-117">See Also</span></span>  
 [<span data-ttu-id="3f0af-118">Ihostsecuritycontext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3f0af-118">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="3f0af-119">Ihostsecuritymanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3f0af-119">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="3f0af-120">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="3f0af-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
