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
ms.openlocfilehash: 93051ca9a0b6f57f41d0d17335a838fe92832d8d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121499"
---
# <a name="ihostsecuritymanagerimpersonateloggedonuser-method"></a><span data-ttu-id="7f254-102">IHostSecurityManager::ImpersonateLoggedOnUser – metoda</span><span class="sxs-lookup"><span data-stu-id="7f254-102">IHostSecurityManager::ImpersonateLoggedOnUser Method</span></span>
<span data-ttu-id="7f254-103">Požaduje, aby se kód spustil s použitím přihlašovacích údajů aktuální identity uživatele.</span><span class="sxs-lookup"><span data-stu-id="7f254-103">Requests that code be executed using the credentials of the current user identity.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f254-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f254-104">Syntax</span></span>  
  
```cpp  
HRESULT ImpersonateLoggedOnUser (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f254-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f254-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="7f254-106">pro Token, který představuje přihlašovací údaje uživatele, který má být zosobněn.</span><span class="sxs-lookup"><span data-stu-id="7f254-106">[in] A token representing the credentials of the user to be impersonated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f254-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7f254-107">Return Value</span></span>  
  
|<span data-ttu-id="7f254-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7f254-108">HRESULT</span></span>|<span data-ttu-id="7f254-109">Popis</span><span class="sxs-lookup"><span data-stu-id="7f254-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7f254-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7f254-110">S_OK</span></span>|<span data-ttu-id="7f254-111">`ImpersonateLoggedOnUser` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="7f254-111">`ImpersonateLoggedOnUser` returned successfully.</span></span>|  
|<span data-ttu-id="7f254-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7f254-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7f254-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="7f254-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7f254-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7f254-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7f254-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="7f254-115">The call timed out.</span></span>|  
|<span data-ttu-id="7f254-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7f254-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7f254-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="7f254-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7f254-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7f254-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7f254-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="7f254-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7f254-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7f254-120">E_FAIL</span></span>|<span data-ttu-id="7f254-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="7f254-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7f254-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="7f254-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7f254-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7f254-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f254-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7f254-124">Remarks</span></span>  
 <span data-ttu-id="7f254-125">Voláním `LogonUser` nebo související funkce Win32 získáte popisovač přihlašovacích údajů aktuální identity uživatele.</span><span class="sxs-lookup"><span data-stu-id="7f254-125">Call `LogonUser` or a related Win32 function to get a handle to the credentials of the current user identity.</span></span>  
  
 <span data-ttu-id="7f254-126">Typ `HANDLE` není kompatibilní s modelem COM, to znamená, že jeho velikost je specifická pro operační systém a vyžaduje vlastní zařazování.</span><span class="sxs-lookup"><span data-stu-id="7f254-126">The `HANDLE` type is not COM-compliant, that is, its size is specific to an operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="7f254-127">Proto je tento token určen pouze pro použití v rámci procesu, mezi CLR a hostitelem.</span><span class="sxs-lookup"><span data-stu-id="7f254-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f254-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7f254-128">Requirements</span></span>  
 <span data-ttu-id="7f254-129">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f254-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f254-130">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7f254-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7f254-131">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7f254-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7f254-132">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f254-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f254-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7f254-133">See also</span></span>

- [<span data-ttu-id="7f254-134">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7f254-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="7f254-135">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7f254-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="7f254-136">RevertToSelf – metoda</span><span class="sxs-lookup"><span data-stu-id="7f254-136">RevertToSelf Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)
