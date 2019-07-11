---
title: EContextType – výčet
ms.date: 03/30/2017
api_name:
- EContextType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EContextType
helpviewer_keywords:
- EContextType enumeration [.NET Framework hosting]
ms.assetid: 92b926a9-b87e-408a-9036-df7b752c9492
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f93f36a78ff5579e131ef4bb3d48f04e806c14de
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779390"
---
# <a name="econtexttype-enumeration"></a><span data-ttu-id="3e038-102">EContextType – výčet</span><span class="sxs-lookup"><span data-stu-id="3e038-102">EContextType Enumeration</span></span>
<span data-ttu-id="3e038-103">Popisuje kontextu zabezpečení aktuálně spuštěné vlákno.</span><span class="sxs-lookup"><span data-stu-id="3e038-103">Describes the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e038-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e038-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a><span data-ttu-id="3e038-105">Členové</span><span class="sxs-lookup"><span data-stu-id="3e038-105">Members</span></span>  
  
|<span data-ttu-id="3e038-106">Člen</span><span class="sxs-lookup"><span data-stu-id="3e038-106">Member</span></span>|<span data-ttu-id="3e038-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3e038-107">Description</span></span>|  
|------------|-----------------|  
|`eCurrentContext`|<span data-ttu-id="3e038-108">Určuje kontext v aktuálním vlákně v době common language runtime (CLR) zavolá [ihostsecuritymanager::getsecuritycontext –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) metoda nebo kontext požadovaný modulem CLR ve volání [ Ihostsecuritymanager::setsecuritycontext –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="3e038-108">Indicates the context on the current thread at the time the common language runtime (CLR) calls the [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) method, or the context requested by the CLR in a call to the [IHostSecurityManager::SetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md) method.</span></span>|  
|`eRestrictedContext`|<span data-ttu-id="3e038-109">Určuje kontext, přes které hostitele má nižší úroveň oprávnění, jako je například systém uvolňování paměti nebo třídu nebo modul konstruktory.</span><span class="sxs-lookup"><span data-stu-id="3e038-109">Indicates a context over which the host has lower privileges, such as the garbage collector, or class or module constructors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e038-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3e038-110">Remarks</span></span>  
 <span data-ttu-id="3e038-111">CLR poskytuje jednu z `EContextType` hodnoty jako hodnotu parametru ve voláních `IHostSecurityManager::GetSecurityContext` a `IHostSecurityManager::SetSecurityContext` metody.</span><span class="sxs-lookup"><span data-stu-id="3e038-111">The CLR supplies one of the `EContextType` values as a parameter value in calls to the `IHostSecurityManager::GetSecurityContext` and `IHostSecurityManager::SetSecurityContext` methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e038-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3e038-112">Requirements</span></span>  
 <span data-ttu-id="3e038-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e038-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e038-114">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3e038-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3e038-115">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3e038-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3e038-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e038-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e038-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3e038-117">See also</span></span>

- [<span data-ttu-id="3e038-118">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3e038-118">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="3e038-119">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3e038-119">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="3e038-120">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="3e038-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
