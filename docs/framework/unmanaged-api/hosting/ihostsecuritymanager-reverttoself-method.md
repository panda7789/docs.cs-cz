---
title: "IHostSecurityManager::RevertToSelf – metoda"
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
- IHostSecurityManager.RevertToSelf
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::RevertToSelf
helpviewer_keywords:
- RevertToSelf method [.NET Framework hosting]
- IHostSecurityManager::RevertToSelf method [.NET Framework hosting]
ms.assetid: 189f28f8-f9a1-4192-aedc-91084e4f8b99
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 765d40cc99269031093e9241ed1bba6c82b9a042
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsecuritymanagerreverttoself-method"></a><span data-ttu-id="7daa9-102">IHostSecurityManager::RevertToSelf – metoda</span><span class="sxs-lookup"><span data-stu-id="7daa9-102">IHostSecurityManager::RevertToSelf Method</span></span>
<span data-ttu-id="7daa9-103">Ukončí zosobnění aktuální identitu uživatele a vrátí původní tokenu vlákna.</span><span class="sxs-lookup"><span data-stu-id="7daa9-103">Terminates impersonation of the current user identity and returns the original thread token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7daa9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7daa9-104">Syntax</span></span>  
  
```  
HRESULT RevertToSelf ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="7daa9-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7daa9-105">Return Value</span></span>  
  
|<span data-ttu-id="7daa9-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7daa9-106">HRESULT</span></span>|<span data-ttu-id="7daa9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7daa9-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7daa9-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="7daa9-108">S_OK</span></span>|<span data-ttu-id="7daa9-109">`RevertToSelf`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="7daa9-109">`RevertToSelf` returned successfully.</span></span>|  
|<span data-ttu-id="7daa9-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7daa9-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7daa9-111">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="7daa9-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7daa9-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7daa9-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7daa9-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="7daa9-113">The call timed out.</span></span>|  
|<span data-ttu-id="7daa9-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7daa9-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7daa9-115">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="7daa9-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7daa9-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7daa9-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7daa9-117">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="7daa9-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7daa9-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7daa9-118">E_FAIL</span></span>|<span data-ttu-id="7daa9-119">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="7daa9-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7daa9-120">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="7daa9-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7daa9-121">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7daa9-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7daa9-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7daa9-122">Remarks</span></span>  
 <span data-ttu-id="7daa9-123">`RevertToSelf`je volána se vraťte do původní tokenu vlákna po starší volání [ImpersonateLoggedOnUser –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="7daa9-123">`RevertToSelf` is called to return to the original thread token, after an earlier call to the [ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7daa9-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7daa9-124">Requirements</span></span>  
 <span data-ttu-id="7daa9-125">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7daa9-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7daa9-126">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7daa9-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7daa9-127">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7daa9-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7daa9-128">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7daa9-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7daa9-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="7daa9-129">See Also</span></span>  
 [<span data-ttu-id="7daa9-130">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7daa9-130">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="7daa9-131">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7daa9-131">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="7daa9-132">ImpersonateLoggedOnUser – metoda</span><span class="sxs-lookup"><span data-stu-id="7daa9-132">ImpersonateLoggedOnUser Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)
