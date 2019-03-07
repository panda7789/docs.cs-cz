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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d17609e585f6e0ecd685d893bb0f8b3e4c0fe0cc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484824"
---
# <a name="ihostsecuritymanagergetsecuritycontext-method"></a><span data-ttu-id="c51a1-102">IHostSecurityManager::GetSecurityContext – metoda</span><span class="sxs-lookup"><span data-stu-id="c51a1-102">IHostSecurityManager::GetSecurityContext Method</span></span>
<span data-ttu-id="c51a1-103">Získá požadovanou [ihostsecuritycontext –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) z hostitele.</span><span class="sxs-lookup"><span data-stu-id="c51a1-103">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c51a1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c51a1-104">Syntax</span></span>  
  
```  
HRESULT GetSecurityContext (  
    [in]  EContextType eContextType,   
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c51a1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c51a1-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="c51a1-106">[in] Jeden z [econtexttype –](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) hodnoty určující, jaký typ kontextu zabezpečení k vrácení.</span><span class="sxs-lookup"><span data-stu-id="c51a1-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of security context to return.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="c51a1-107">[out] Adresa ukazatele rozhraní na `IHostSecurityContext` z `eContextType`.</span><span class="sxs-lookup"><span data-stu-id="c51a1-107">[out] The address of an interface pointer to the `IHostSecurityContext` of `eContextType`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c51a1-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c51a1-108">Return Value</span></span>  
  
|<span data-ttu-id="c51a1-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c51a1-109">HRESULT</span></span>|<span data-ttu-id="c51a1-110">Popis</span><span class="sxs-lookup"><span data-stu-id="c51a1-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c51a1-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c51a1-111">S_OK</span></span>|<span data-ttu-id="c51a1-112">`GetSecurityContext` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="c51a1-112">`GetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="c51a1-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c51a1-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c51a1-114">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c51a1-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c51a1-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c51a1-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c51a1-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="c51a1-116">The call timed out.</span></span>|  
|<span data-ttu-id="c51a1-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c51a1-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c51a1-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="c51a1-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c51a1-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c51a1-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c51a1-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="c51a1-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c51a1-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c51a1-121">E_FAIL</span></span>|<span data-ttu-id="c51a1-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="c51a1-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c51a1-123">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="c51a1-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c51a1-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c51a1-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c51a1-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c51a1-125">Remarks</span></span>  
 <span data-ttu-id="c51a1-126">Hostitele přístup můžete řídit všechny kódu tokeny vlákna CLR a uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="c51a1-126">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="c51a1-127">Můžete také zajistit zabezpečení úplné informace o kontextu je předán přes asynchronní operace nebo body kódu s přístup ke kódu s omezeným přístupem.</span><span class="sxs-lookup"><span data-stu-id="c51a1-127">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="c51a1-128">`IHostSecurityContext` zapouzdřuje tyto informace kontextu zabezpečení, což je neprůhledný modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="c51a1-128">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span> <span data-ttu-id="c51a1-129">Modul CLR shromažďuje tyto informace a přesouvá ji napříč vlákna fondu pracovních procesů položky odeslání, spuštění finalizační metody a modulu a třída konstrukce.</span><span class="sxs-lookup"><span data-stu-id="c51a1-129">The CLR captures this information and moves it across thread pool worker item dispatch, finalizer execution, and module and class construction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c51a1-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c51a1-130">Requirements</span></span>  
 <span data-ttu-id="c51a1-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c51a1-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c51a1-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c51a1-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c51a1-133">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c51a1-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c51a1-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c51a1-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c51a1-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c51a1-135">See also</span></span>
- [<span data-ttu-id="c51a1-136">EContextType – výčet</span><span class="sxs-lookup"><span data-stu-id="c51a1-136">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)
- [<span data-ttu-id="c51a1-137">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c51a1-137">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="c51a1-138">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c51a1-138">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
