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
ms.openlocfilehash: f098d8462229a405d5775203368478c7ee7e9f3c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769398"
---
# <a name="ihostsecuritymanagerreverttoself-method"></a><span data-ttu-id="6d914-102">IHostSecurityManager::RevertToSelf – metoda</span><span class="sxs-lookup"><span data-stu-id="6d914-102">IHostSecurityManager::RevertToSelf Method</span></span>
<span data-ttu-id="6d914-103">Zosobnění aktuální identitu uživatele se ukončí a vrátí původní token vlákna.</span><span class="sxs-lookup"><span data-stu-id="6d914-103">Terminates impersonation of the current user identity and returns the original thread token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d914-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d914-104">Syntax</span></span>  
  
```cpp  
HRESULT RevertToSelf ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="6d914-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6d914-105">Return Value</span></span>  
  
|<span data-ttu-id="6d914-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6d914-106">HRESULT</span></span>|<span data-ttu-id="6d914-107">Popis</span><span class="sxs-lookup"><span data-stu-id="6d914-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6d914-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="6d914-108">S_OK</span></span>|<span data-ttu-id="6d914-109">`RevertToSelf` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="6d914-109">`RevertToSelf` returned successfully.</span></span>|  
|<span data-ttu-id="6d914-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6d914-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6d914-111">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="6d914-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6d914-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6d914-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6d914-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="6d914-113">The call timed out.</span></span>|  
|<span data-ttu-id="6d914-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6d914-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6d914-115">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="6d914-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6d914-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6d914-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6d914-117">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="6d914-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6d914-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6d914-118">E_FAIL</span></span>|<span data-ttu-id="6d914-119">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="6d914-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6d914-120">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="6d914-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6d914-121">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6d914-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d914-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6d914-122">Remarks</span></span>  
 <span data-ttu-id="6d914-123">`RevertToSelf` je volána k vrácení k původní tokenu vlákna po dřívějším volání [ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="6d914-123">`RevertToSelf` is called to return to the original thread token, after an earlier call to the [ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d914-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6d914-124">Requirements</span></span>  
 <span data-ttu-id="6d914-125">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d914-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d914-126">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6d914-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6d914-127">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6d914-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6d914-128">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d914-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d914-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6d914-129">See also</span></span>

- [<span data-ttu-id="6d914-130">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6d914-130">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="6d914-131">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6d914-131">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="6d914-132">ImpersonateLoggedOnUser – metoda</span><span class="sxs-lookup"><span data-stu-id="6d914-132">ImpersonateLoggedOnUser Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)
