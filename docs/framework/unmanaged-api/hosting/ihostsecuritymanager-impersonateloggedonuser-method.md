---
title: "IHostSecurityManager::ImpersonateLoggedOnUser – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager.ImpersonateLoggedOnUser
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager::ImpersonateLoggedOnUser
helpviewer_keywords:
- ImpersonateLoggedOnUser method [.NET Framework hosting]
- IHostSecurityManager::ImpersonateLoggedOnUser method [.NET Framework hosting]
ms.assetid: acc49ba0-f1d9-45ad-871f-9d053a89dcbe
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8c5956dcad6908f0117de7f5ff0c6632ad3bb925
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsecuritymanagerimpersonateloggedonuser-method"></a><span data-ttu-id="6c3e4-102">IHostSecurityManager::ImpersonateLoggedOnUser – metoda</span><span class="sxs-lookup"><span data-stu-id="6c3e4-102">IHostSecurityManager::ImpersonateLoggedOnUser Method</span></span>
<span data-ttu-id="6c3e4-103">Požadavky kódu být spuštěn pomocí pověření aktuální identita uživatele.</span><span class="sxs-lookup"><span data-stu-id="6c3e4-103">Requests that code be executed using the credentials of the current user identity.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c3e4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c3e4-104">Syntax</span></span>  
  
```  
HRESULT ImpersonateLoggedOnUser (  
    [in] HANDLE hToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c3e4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c3e4-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="6c3e4-106">[v] Token představující přihlašovací údaje uživatele k zosobnit.</span><span class="sxs-lookup"><span data-stu-id="6c3e4-106">[in] A token representing the credentials of the user to be impersonated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c3e4-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6c3e4-107">Return Value</span></span>  
  
|<span data-ttu-id="6c3e4-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6c3e4-108">HRESULT</span></span>|<span data-ttu-id="6c3e4-109">Popis</span><span class="sxs-lookup"><span data-stu-id="6c3e4-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6c3e4-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6c3e4-110">S_OK</span></span>|<span data-ttu-id="6c3e4-111">`ImpersonateLoggedOnUser`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="6c3e4-111">`ImpersonateLoggedOnUser` returned successfully.</span></span>|  
|<span data-ttu-id="6c3e4-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6c3e4-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6c3e4-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="6c3e4-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6c3e4-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6c3e4-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6c3e4-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="6c3e4-115">The call timed out.</span></span>|  
|<span data-ttu-id="6c3e4-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6c3e4-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6c3e4-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="6c3e4-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6c3e4-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6c3e4-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6c3e4-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="6c3e4-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6c3e4-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6c3e4-120">E_FAIL</span></span>|<span data-ttu-id="6c3e4-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="6c3e4-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6c3e4-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="6c3e4-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6c3e4-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6c3e4-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c3e4-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6c3e4-124">Remarks</span></span>  
 <span data-ttu-id="6c3e4-125">Volání `LogonUser` nebo související funkce Win32 se získat popisovač pro přihlašovací údaje aktuální identita uživatele.</span><span class="sxs-lookup"><span data-stu-id="6c3e4-125">Call `LogonUser` or a related Win32 function to get a handle to the credentials of the current user identity.</span></span>  
  
 <span data-ttu-id="6c3e4-126">`HANDLE` Typ není kompatibilní se standardem COM, který je jeho velikost je specifické pro operační systém a vyžaduje vlastní zařazování.</span><span class="sxs-lookup"><span data-stu-id="6c3e4-126">The `HANDLE` type is not COM-compliant, that is, its size is specific to an operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="6c3e4-127">Tento token je proto pro použití pouze v rámci procesu mezi modulu CLR a hostitelem.</span><span class="sxs-lookup"><span data-stu-id="6c3e4-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c3e4-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6c3e4-128">Requirements</span></span>  
 <span data-ttu-id="6c3e4-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c3e4-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c3e4-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6c3e4-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6c3e4-131">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6c3e4-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c3e4-132">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c3e4-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c3e4-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c3e4-133">See Also</span></span>  
 [<span data-ttu-id="6c3e4-134">Ihostsecuritycontext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c3e4-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="6c3e4-135">Ihostsecuritymanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c3e4-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="6c3e4-136">RevertToSelf – metoda</span><span class="sxs-lookup"><span data-stu-id="6c3e4-136">RevertToSelf Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)
