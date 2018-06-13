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
ms.openlocfilehash: 71f5cdfaf47c55107980edf089f8964c5936fb23
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440983"
---
# <a name="ihostsecuritymanagersetthreadtoken-method"></a><span data-ttu-id="db264-102">IHostSecurityManager::SetThreadToken – metoda</span><span class="sxs-lookup"><span data-stu-id="db264-102">IHostSecurityManager::SetThreadToken Method</span></span>
<span data-ttu-id="db264-103">Nastaví popisovač pro aktuálně prováděné vlákno.</span><span class="sxs-lookup"><span data-stu-id="db264-103">Sets a handle for the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db264-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db264-104">Syntax</span></span>  
  
```  
HRESULT SetThreadToken (  
    [in] HANDLE hToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db264-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="db264-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="db264-106">[v] Popisovač pro token, který má nastavit pro aktuálně prováděné vlákno.</span><span class="sxs-lookup"><span data-stu-id="db264-106">[in] A handle to the token to set for the currently executing thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db264-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="db264-107">Return Value</span></span>  
  
|<span data-ttu-id="db264-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="db264-108">HRESULT</span></span>|<span data-ttu-id="db264-109">Popis</span><span class="sxs-lookup"><span data-stu-id="db264-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="db264-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="db264-110">S_OK</span></span>|<span data-ttu-id="db264-111">`SetThreadToken` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="db264-111">`SetThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="db264-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="db264-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="db264-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="db264-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="db264-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="db264-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="db264-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="db264-115">The call timed out.</span></span>|  
|<span data-ttu-id="db264-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="db264-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="db264-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="db264-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="db264-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="db264-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="db264-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="db264-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="db264-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="db264-120">E_FAIL</span></span>|<span data-ttu-id="db264-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="db264-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="db264-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="db264-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="db264-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="db264-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db264-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="db264-124">Remarks</span></span>  
 <span data-ttu-id="db264-125">`IHostSecurityManager::SetThreadToken` chová podobně jako odpovídající funkce Win32 se stejným názvem, s tím rozdílem, že funkce Win32 umožňuje předat libovolný vláken v popisovač volajícímu, při `IHostSecurityManager::SetThreadToken` token můžete přiřadit pouze k aktuálně prováděné vlákno.</span><span class="sxs-lookup"><span data-stu-id="db264-125">`IHostSecurityManager::SetThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::SetThreadToken` can associate a token only with the currently executing thread.</span></span>  
  
 <span data-ttu-id="db264-126">`HANDLE` Typ není kompatibilní se standardem COM; to znamená, jeho velikost je specifické pro operační systém a vyžaduje vlastní zařazování.</span><span class="sxs-lookup"><span data-stu-id="db264-126">The `HANDLE` type is not COM-compliant; that is, its size is specific to an operating system and it requires custom marshaling.</span></span> <span data-ttu-id="db264-127">Tento token je proto pro použití pouze v rámci procesu mezi modulu CLR a hostitelem.</span><span class="sxs-lookup"><span data-stu-id="db264-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db264-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="db264-128">Requirements</span></span>  
 <span data-ttu-id="db264-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db264-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db264-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="db264-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="db264-131">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="db264-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db264-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db264-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db264-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="db264-133">See Also</span></span>  
 [<span data-ttu-id="db264-134">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="db264-134">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="db264-135">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="db264-135">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
