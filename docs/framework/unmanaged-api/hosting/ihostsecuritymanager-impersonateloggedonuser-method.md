---
title: IHostSecurityManager::ImpersonateLoggedOnUser – metoda
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.ImpersonateLoggedOnUser
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::ImpersonateLoggedOnUser
helpviewer_keywords:
- ImpersonateLoggedOnUser method [.NET Framework hosting]
- IHostSecurityManager::ImpersonateLoggedOnUser method [.NET Framework hosting]
ms.assetid: acc49ba0-f1d9-45ad-871f-9d053a89dcbe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3e4a90e8cd50ef1b3324aed35ae5cc34225bb2f7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471352"
---
# <a name="ihostsecuritymanagerimpersonateloggedonuser-method"></a><span data-ttu-id="10830-102">IHostSecurityManager::ImpersonateLoggedOnUser – metoda</span><span class="sxs-lookup"><span data-stu-id="10830-102">IHostSecurityManager::ImpersonateLoggedOnUser Method</span></span>
<span data-ttu-id="10830-103">Požadavky, který kód spuštěn pomocí pověření aktuální identitu uživatele.</span><span class="sxs-lookup"><span data-stu-id="10830-103">Requests that code be executed using the credentials of the current user identity.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10830-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10830-104">Syntax</span></span>  
  
```  
HRESULT ImpersonateLoggedOnUser (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10830-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="10830-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="10830-106">[in] Token představující přihlašovací údaje uživatele, kterého chcete zosobnit.</span><span class="sxs-lookup"><span data-stu-id="10830-106">[in] A token representing the credentials of the user to be impersonated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="10830-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="10830-107">Return Value</span></span>  
  
|<span data-ttu-id="10830-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="10830-108">HRESULT</span></span>|<span data-ttu-id="10830-109">Popis</span><span class="sxs-lookup"><span data-stu-id="10830-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="10830-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="10830-110">S_OK</span></span>|<span data-ttu-id="10830-111">`ImpersonateLoggedOnUser` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="10830-111">`ImpersonateLoggedOnUser` returned successfully.</span></span>|  
|<span data-ttu-id="10830-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="10830-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="10830-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="10830-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="10830-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="10830-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="10830-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="10830-115">The call timed out.</span></span>|  
|<span data-ttu-id="10830-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="10830-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="10830-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="10830-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="10830-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="10830-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="10830-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="10830-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="10830-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="10830-120">E_FAIL</span></span>|<span data-ttu-id="10830-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="10830-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="10830-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="10830-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="10830-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="10830-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10830-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="10830-124">Remarks</span></span>  
 <span data-ttu-id="10830-125">Volání `LogonUser` nebo související funkce Win32, chcete-li získat popisovač přihlašovacích údajů aktuální identitu uživatele.</span><span class="sxs-lookup"><span data-stu-id="10830-125">Call `LogonUser` or a related Win32 function to get a handle to the credentials of the current user identity.</span></span>  
  
 <span data-ttu-id="10830-126">`HANDLE` Typ není kompatibilní s rozhraním modelu COM, to znamená, jeho velikost je specifické pro operační systém, a vyžaduje vlastní zařazování.</span><span class="sxs-lookup"><span data-stu-id="10830-126">The `HANDLE` type is not COM-compliant, that is, its size is specific to an operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="10830-127">Proto je tento token pro použití pouze v rámci procesu mezi CLR a hostitelem.</span><span class="sxs-lookup"><span data-stu-id="10830-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10830-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="10830-128">Requirements</span></span>  
 <span data-ttu-id="10830-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10830-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10830-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="10830-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="10830-131">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="10830-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="10830-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10830-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10830-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10830-133">See also</span></span>
- [<span data-ttu-id="10830-134">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="10830-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="10830-135">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="10830-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="10830-136">RevertToSelf – metoda</span><span class="sxs-lookup"><span data-stu-id="10830-136">RevertToSelf Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)
