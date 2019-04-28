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
ms.openlocfilehash: c67471c0d88ccffbfe9b7c77809124452ccc2e5b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61696636"
---
# <a name="ihostsecuritymanagersetthreadtoken-method"></a><span data-ttu-id="fc3be-102">IHostSecurityManager::SetThreadToken – metoda</span><span class="sxs-lookup"><span data-stu-id="fc3be-102">IHostSecurityManager::SetThreadToken Method</span></span>
<span data-ttu-id="fc3be-103">Nastaví obslužnou rutinu pro aktuálně spuštěné vlákno.</span><span class="sxs-lookup"><span data-stu-id="fc3be-103">Sets a handle for the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc3be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc3be-104">Syntax</span></span>  
  
```  
HRESULT SetThreadToken (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc3be-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc3be-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="fc3be-106">[in] Popisovač pro token, který má nastavit pro aktuálně spuštěné vlákno.</span><span class="sxs-lookup"><span data-stu-id="fc3be-106">[in] A handle to the token to set for the currently executing thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc3be-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fc3be-107">Return Value</span></span>  
  
|<span data-ttu-id="fc3be-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fc3be-108">HRESULT</span></span>|<span data-ttu-id="fc3be-109">Popis</span><span class="sxs-lookup"><span data-stu-id="fc3be-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fc3be-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fc3be-110">S_OK</span></span>|<span data-ttu-id="fc3be-111">`SetThreadToken` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="fc3be-111">`SetThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="fc3be-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fc3be-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fc3be-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="fc3be-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fc3be-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fc3be-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fc3be-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="fc3be-115">The call timed out.</span></span>|  
|<span data-ttu-id="fc3be-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fc3be-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fc3be-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="fc3be-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fc3be-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fc3be-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fc3be-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="fc3be-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fc3be-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fc3be-120">E_FAIL</span></span>|<span data-ttu-id="fc3be-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="fc3be-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fc3be-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="fc3be-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fc3be-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fc3be-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc3be-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fc3be-124">Remarks</span></span>  
 <span data-ttu-id="fc3be-125">`IHostSecurityManager::SetThreadToken` se chová podobně jako odpovídající funkce Win32 se stejným názvem, s tím rozdílem, že funkci Win32 umožňuje volajícímu a zajistěte tak předání popisovač do libovolného vlákna, zatímco `IHostSecurityManager::SetThreadToken` můžete přidružit token pouze aktuálně spuštěné vlákno.</span><span class="sxs-lookup"><span data-stu-id="fc3be-125">`IHostSecurityManager::SetThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::SetThreadToken` can associate a token only with the currently executing thread.</span></span>  
  
 <span data-ttu-id="fc3be-126">`HANDLE` Typ není kompatibilní s rozhraním COM; to znamená, jeho velikost je specifické pro operační systém a vyžaduje vlastní zařazování.</span><span class="sxs-lookup"><span data-stu-id="fc3be-126">The `HANDLE` type is not COM-compliant; that is, its size is specific to an operating system and it requires custom marshaling.</span></span> <span data-ttu-id="fc3be-127">Proto je tento token pro použití pouze v rámci procesu mezi CLR a hostitelem.</span><span class="sxs-lookup"><span data-stu-id="fc3be-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc3be-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fc3be-128">Requirements</span></span>  
 <span data-ttu-id="fc3be-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc3be-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc3be-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fc3be-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fc3be-131">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fc3be-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fc3be-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc3be-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc3be-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fc3be-133">See also</span></span>

- [<span data-ttu-id="fc3be-134">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fc3be-134">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="fc3be-135">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fc3be-135">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
