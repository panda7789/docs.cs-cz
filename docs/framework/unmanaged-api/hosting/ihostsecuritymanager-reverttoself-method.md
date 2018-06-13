---
title: IHostSecurityManager::RevertToSelf – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c34d9243e4ed7ed2492784154b157189c7d22cd2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440577"
---
# <a name="ihostsecuritymanagerreverttoself-method"></a><span data-ttu-id="0ae04-102">IHostSecurityManager::RevertToSelf – metoda</span><span class="sxs-lookup"><span data-stu-id="0ae04-102">IHostSecurityManager::RevertToSelf Method</span></span>
<span data-ttu-id="0ae04-103">Ukončí zosobnění aktuální identitu uživatele a vrátí původní tokenu vlákna.</span><span class="sxs-lookup"><span data-stu-id="0ae04-103">Terminates impersonation of the current user identity and returns the original thread token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ae04-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ae04-104">Syntax</span></span>  
  
```  
HRESULT RevertToSelf ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="0ae04-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0ae04-105">Return Value</span></span>  
  
|<span data-ttu-id="0ae04-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0ae04-106">HRESULT</span></span>|<span data-ttu-id="0ae04-107">Popis</span><span class="sxs-lookup"><span data-stu-id="0ae04-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0ae04-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="0ae04-108">S_OK</span></span>|<span data-ttu-id="0ae04-109">`RevertToSelf` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="0ae04-109">`RevertToSelf` returned successfully.</span></span>|  
|<span data-ttu-id="0ae04-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0ae04-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0ae04-111">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="0ae04-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0ae04-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0ae04-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0ae04-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="0ae04-113">The call timed out.</span></span>|  
|<span data-ttu-id="0ae04-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0ae04-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0ae04-115">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="0ae04-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0ae04-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0ae04-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0ae04-117">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="0ae04-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0ae04-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0ae04-118">E_FAIL</span></span>|<span data-ttu-id="0ae04-119">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="0ae04-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0ae04-120">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="0ae04-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0ae04-121">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0ae04-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ae04-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0ae04-122">Remarks</span></span>  
 <span data-ttu-id="0ae04-123">`RevertToSelf` je volána se vraťte do původní tokenu vlákna po starší volání [ImpersonateLoggedOnUser –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="0ae04-123">`RevertToSelf` is called to return to the original thread token, after an earlier call to the [ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ae04-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0ae04-124">Requirements</span></span>  
 <span data-ttu-id="0ae04-125">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ae04-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ae04-126">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0ae04-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0ae04-127">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0ae04-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0ae04-128">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ae04-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ae04-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ae04-129">See Also</span></span>  
 [<span data-ttu-id="0ae04-130">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0ae04-130">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="0ae04-131">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0ae04-131">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="0ae04-132">ImpersonateLoggedOnUser – metoda</span><span class="sxs-lookup"><span data-stu-id="0ae04-132">ImpersonateLoggedOnUser Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)
