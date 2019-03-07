---
title: IHostSecurityManager::SetThreadToken – metoda
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.SetThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::SetThreadToken
helpviewer_keywords:
- SetThreadToken method [.NET Framework hosting]
- IHostSecurityManager::SetThreadToken method [.NET Framework hosting]
ms.assetid: e951c345-8a86-4587-911b-a1a57bc6428a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e06a76b4d51245388bf36b8127a470f55ca645fa
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494698"
---
# <a name="ihostsecuritymanagersetthreadtoken-method"></a><span data-ttu-id="d9e44-102">IHostSecurityManager::SetThreadToken – metoda</span><span class="sxs-lookup"><span data-stu-id="d9e44-102">IHostSecurityManager::SetThreadToken Method</span></span>
<span data-ttu-id="d9e44-103">Nastaví obslužnou rutinu pro aktuálně spuštěné vlákno.</span><span class="sxs-lookup"><span data-stu-id="d9e44-103">Sets a handle for the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9e44-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9e44-104">Syntax</span></span>  
  
```  
HRESULT SetThreadToken (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9e44-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d9e44-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="d9e44-106">[in] Popisovač pro token, který má nastavit pro aktuálně spuštěné vlákno.</span><span class="sxs-lookup"><span data-stu-id="d9e44-106">[in] A handle to the token to set for the currently executing thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9e44-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d9e44-107">Return Value</span></span>  
  
|<span data-ttu-id="d9e44-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d9e44-108">HRESULT</span></span>|<span data-ttu-id="d9e44-109">Popis</span><span class="sxs-lookup"><span data-stu-id="d9e44-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d9e44-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d9e44-110">S_OK</span></span>|<span data-ttu-id="d9e44-111">`SetThreadToken` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="d9e44-111">`SetThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="d9e44-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d9e44-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d9e44-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="d9e44-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d9e44-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d9e44-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d9e44-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="d9e44-115">The call timed out.</span></span>|  
|<span data-ttu-id="d9e44-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d9e44-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d9e44-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="d9e44-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d9e44-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d9e44-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d9e44-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="d9e44-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d9e44-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d9e44-120">E_FAIL</span></span>|<span data-ttu-id="d9e44-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="d9e44-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d9e44-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="d9e44-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d9e44-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d9e44-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9e44-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d9e44-124">Remarks</span></span>  
 <span data-ttu-id="d9e44-125">`IHostSecurityManager::SetThreadToken` se chová podobně jako odpovídající funkce Win32 se stejným názvem, s tím rozdílem, že funkci Win32 umožňuje volajícímu a zajistěte tak předání popisovač do libovolného vlákna, zatímco `IHostSecurityManager::SetThreadToken` můžete přidružit token pouze aktuálně spuštěné vlákno.</span><span class="sxs-lookup"><span data-stu-id="d9e44-125">`IHostSecurityManager::SetThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::SetThreadToken` can associate a token only with the currently executing thread.</span></span>  
  
 <span data-ttu-id="d9e44-126">`HANDLE` Typ není kompatibilní s rozhraním COM; to znamená, jeho velikost je specifické pro operační systém a vyžaduje vlastní zařazování.</span><span class="sxs-lookup"><span data-stu-id="d9e44-126">The `HANDLE` type is not COM-compliant; that is, its size is specific to an operating system and it requires custom marshaling.</span></span> <span data-ttu-id="d9e44-127">Proto je tento token pro použití pouze v rámci procesu mezi CLR a hostitelem.</span><span class="sxs-lookup"><span data-stu-id="d9e44-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9e44-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d9e44-128">Requirements</span></span>  
 <span data-ttu-id="d9e44-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9e44-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9e44-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d9e44-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d9e44-131">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d9e44-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9e44-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9e44-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9e44-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d9e44-133">See also</span></span>
- [<span data-ttu-id="d9e44-134">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d9e44-134">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="d9e44-135">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d9e44-135">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
