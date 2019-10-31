---
title: IHostSecurityManager::GetSecurityContext – metoda
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.GetSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::GetSecurityContext
helpviewer_keywords:
- GetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::GetSecurityContext method [.NET Framework hosting]
ms.assetid: 958970d6-f6a2-4b84-b32a-f555cbaf8f61
topic_type:
- apiref
ms.openlocfilehash: 66aab8081a5cce8c5ba986470bc91eb0604781a5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121505"
---
# <a name="ihostsecuritymanagergetsecuritycontext-method"></a><span data-ttu-id="86d4a-102">IHostSecurityManager::GetSecurityContext – metoda</span><span class="sxs-lookup"><span data-stu-id="86d4a-102">IHostSecurityManager::GetSecurityContext Method</span></span>
<span data-ttu-id="86d4a-103">Získá požadovaná [IHostSecurityContext –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) z hostitele.</span><span class="sxs-lookup"><span data-stu-id="86d4a-103">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86d4a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86d4a-104">Syntax</span></span>  
  
```cpp
HRESULT GetSecurityContext (  
    [in]  EContextType eContextType,   
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86d4a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="86d4a-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="86d4a-106">pro Jedna z hodnot [EContextType –](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) , která označuje typ kontextu zabezpečení, který se má vrátit.</span><span class="sxs-lookup"><span data-stu-id="86d4a-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of security context to return.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="86d4a-107">mimo Adresa ukazatele rozhraní na `IHostSecurityContext` `eContextType`.</span><span class="sxs-lookup"><span data-stu-id="86d4a-107">[out] The address of an interface pointer to the `IHostSecurityContext` of `eContextType`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86d4a-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="86d4a-108">Return Value</span></span>  
  
|<span data-ttu-id="86d4a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="86d4a-109">HRESULT</span></span>|<span data-ttu-id="86d4a-110">Popis</span><span class="sxs-lookup"><span data-stu-id="86d4a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="86d4a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="86d4a-111">S_OK</span></span>|<span data-ttu-id="86d4a-112">`GetSecurityContext` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="86d4a-112">`GetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="86d4a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="86d4a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="86d4a-114">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="86d4a-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="86d4a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="86d4a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="86d4a-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="86d4a-116">The call timed out.</span></span>|  
|<span data-ttu-id="86d4a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="86d4a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="86d4a-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="86d4a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="86d4a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="86d4a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="86d4a-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="86d4a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="86d4a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="86d4a-121">E_FAIL</span></span>|<span data-ttu-id="86d4a-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="86d4a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="86d4a-123">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="86d4a-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="86d4a-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="86d4a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86d4a-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="86d4a-125">Remarks</span></span>  
 <span data-ttu-id="86d4a-126">Hostitel může řídit veškerý přístup kódu k tokenům vláken jak CLR, tak i uživatelský kód.</span><span class="sxs-lookup"><span data-stu-id="86d4a-126">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="86d4a-127">Může také zajistit, aby byly kompletní informace o kontextu zabezpečení předány přes asynchronní operace nebo body kódu s omezeným přístupem ke kódu.</span><span class="sxs-lookup"><span data-stu-id="86d4a-127">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="86d4a-128">`IHostSecurityContext` zapouzdřuje tyto informace kontextu zabezpečení, které jsou neprůhledné pro CLR.</span><span class="sxs-lookup"><span data-stu-id="86d4a-128">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span> <span data-ttu-id="86d4a-129">Modul CLR tyto informace zachytí a přesune je napříč fondem vláken pracovní položky, provádění finalizační metody a konstrukce modulu a třídy.</span><span class="sxs-lookup"><span data-stu-id="86d4a-129">The CLR captures this information and moves it across thread pool worker item dispatch, finalizer execution, and module and class construction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86d4a-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="86d4a-130">Requirements</span></span>  
 <span data-ttu-id="86d4a-131">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86d4a-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86d4a-132">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="86d4a-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="86d4a-133">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="86d4a-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="86d4a-134">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86d4a-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86d4a-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="86d4a-135">See also</span></span>

- [<span data-ttu-id="86d4a-136">EContextType – výčet</span><span class="sxs-lookup"><span data-stu-id="86d4a-136">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)
- [<span data-ttu-id="86d4a-137">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="86d4a-137">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="86d4a-138">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="86d4a-138">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
