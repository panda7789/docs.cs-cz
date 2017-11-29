---
title: "IHostSecurityManager::GetSecurityContext – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager.GetSecurityContext
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager::GetSecurityContext
helpviewer_keywords:
- GetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::GetSecurityContext method [.NET Framework hosting]
ms.assetid: 958970d6-f6a2-4b84-b32a-f555cbaf8f61
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b150700c50842791a2413688583e7e1289852d62
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsecuritymanagergetsecuritycontext-method"></a><span data-ttu-id="ff3ee-102">IHostSecurityManager::GetSecurityContext – metoda</span><span class="sxs-lookup"><span data-stu-id="ff3ee-102">IHostSecurityManager::GetSecurityContext Method</span></span>
<span data-ttu-id="ff3ee-103">Získá požadované [ihostsecuritycontext –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) z hostitele.</span><span class="sxs-lookup"><span data-stu-id="ff3ee-103">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff3ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff3ee-104">Syntax</span></span>  
  
```  
HRESULT GetSecurityContext (  
    [in]  EContextType eContextType,   
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff3ee-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff3ee-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="ff3ee-106">[v] Jeden z [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) hodnoty, která určuje, jaký typ kontext zabezpečení, který má vrátit.</span><span class="sxs-lookup"><span data-stu-id="ff3ee-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of security context to return.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="ff3ee-107">[out] Na adresu ukazatele rozhraní na `IHostSecurityContext` z `eContextType`.</span><span class="sxs-lookup"><span data-stu-id="ff3ee-107">[out] The address of an interface pointer to the `IHostSecurityContext` of `eContextType`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ff3ee-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ff3ee-108">Return Value</span></span>  
  
|<span data-ttu-id="ff3ee-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ff3ee-109">HRESULT</span></span>|<span data-ttu-id="ff3ee-110">Popis</span><span class="sxs-lookup"><span data-stu-id="ff3ee-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ff3ee-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ff3ee-111">S_OK</span></span>|<span data-ttu-id="ff3ee-112">`GetSecurityContext`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="ff3ee-112">`GetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="ff3ee-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ff3ee-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ff3ee-114">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="ff3ee-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ff3ee-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ff3ee-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ff3ee-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="ff3ee-116">The call timed out.</span></span>|  
|<span data-ttu-id="ff3ee-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ff3ee-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ff3ee-118">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="ff3ee-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ff3ee-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ff3ee-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ff3ee-120">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="ff3ee-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ff3ee-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ff3ee-121">E_FAIL</span></span>|<span data-ttu-id="ff3ee-122">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="ff3ee-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ff3ee-123">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="ff3ee-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ff3ee-124">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ff3ee-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff3ee-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ff3ee-125">Remarks</span></span>  
 <span data-ttu-id="ff3ee-126">Hostitel můžou řídit všechny kódu přístup k vlákno tokeny kódem CLR i uživateli.</span><span class="sxs-lookup"><span data-stu-id="ff3ee-126">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="ff3ee-127">Ho můžete také zajistit, že dokončení zabezpečení informace o kontextu je předán přes asynchronních operací nebo body kódu s přístupem kód s omezeným přístupem.</span><span class="sxs-lookup"><span data-stu-id="ff3ee-127">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="ff3ee-128">`IHostSecurityContext`zapouzdří tato informace kontextu zabezpečení, která je plné krytí modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="ff3ee-128">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span> <span data-ttu-id="ff3ee-129">Modul CLR zaznamená tyto informace a přesouvá ji napříč vlákno fondu pracovní položka odesílání, provádění finalizační metodu a modul a třída konstrukce.</span><span class="sxs-lookup"><span data-stu-id="ff3ee-129">The CLR captures this information and moves it across thread pool worker item dispatch, finalizer execution, and module and class construction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff3ee-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ff3ee-130">Requirements</span></span>  
 <span data-ttu-id="ff3ee-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff3ee-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff3ee-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ff3ee-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ff3ee-133">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ff3ee-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ff3ee-134">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff3ee-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff3ee-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff3ee-135">See Also</span></span>  
 [<span data-ttu-id="ff3ee-136">EContextType – výčet</span><span class="sxs-lookup"><span data-stu-id="ff3ee-136">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)  
 [<span data-ttu-id="ff3ee-137">Ihostsecuritycontext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ff3ee-137">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="ff3ee-138">Ihostsecuritymanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ff3ee-138">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
