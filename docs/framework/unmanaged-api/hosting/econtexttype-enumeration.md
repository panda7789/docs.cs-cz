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
ms.openlocfilehash: 5e82f542bdc364a52fc558e582134a7d8d554ec3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131148"
---
# <a name="econtexttype-enumeration"></a><span data-ttu-id="04a17-102">EContextType – výčet</span><span class="sxs-lookup"><span data-stu-id="04a17-102">EContextType Enumeration</span></span>
<span data-ttu-id="04a17-103">Popisuje kontext zabezpečení aktuálně zpracovávaného vlákna.</span><span class="sxs-lookup"><span data-stu-id="04a17-103">Describes the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04a17-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04a17-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a><span data-ttu-id="04a17-105">Členové</span><span class="sxs-lookup"><span data-stu-id="04a17-105">Members</span></span>  
  
|<span data-ttu-id="04a17-106">Člen</span><span class="sxs-lookup"><span data-stu-id="04a17-106">Member</span></span>|<span data-ttu-id="04a17-107">Popis</span><span class="sxs-lookup"><span data-stu-id="04a17-107">Description</span></span>|  
|------------|-----------------|  
|`eCurrentContext`|<span data-ttu-id="04a17-108">Označuje kontext v aktuálním vlákně v době, kdy modul CLR (Common Language Runtime) volá metodu [IHostSecurityManager:: GetSecurityContext –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) , nebo kontext požadovaný modulem CLR ve volání metody [IHostSecurityManager:: SetSecurityContext –. ](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)metoda.</span><span class="sxs-lookup"><span data-stu-id="04a17-108">Indicates the context on the current thread at the time the common language runtime (CLR) calls the [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) method, or the context requested by the CLR in a call to the [IHostSecurityManager::SetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md) method.</span></span>|  
|`eRestrictedContext`|<span data-ttu-id="04a17-109">Označuje kontext, přes který má hostitel nižší oprávnění, jako je uvolňování paměti nebo konstruktory třídy nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="04a17-109">Indicates a context over which the host has lower privileges, such as the garbage collector, or class or module constructors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04a17-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="04a17-110">Remarks</span></span>  
 <span data-ttu-id="04a17-111">Modul CLR poskytuje jednu z hodnot `EContextType` jako hodnotu parametru v volání metody `IHostSecurityManager::GetSecurityContext` a `IHostSecurityManager::SetSecurityContext`.</span><span class="sxs-lookup"><span data-stu-id="04a17-111">The CLR supplies one of the `EContextType` values as a parameter value in calls to the `IHostSecurityManager::GetSecurityContext` and `IHostSecurityManager::SetSecurityContext` methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04a17-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="04a17-112">Requirements</span></span>  
 <span data-ttu-id="04a17-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04a17-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04a17-114">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="04a17-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="04a17-115">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="04a17-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="04a17-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04a17-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04a17-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04a17-117">See also</span></span>

- [<span data-ttu-id="04a17-118">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="04a17-118">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="04a17-119">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="04a17-119">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="04a17-120">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="04a17-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
