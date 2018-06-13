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
ms.openlocfilehash: c8b6c110a4e7754a6bcca326b659599ffa2caedf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440547"
---
# <a name="ihostsecuritymanagergetsecuritycontext-method"></a><span data-ttu-id="17e0d-102">IHostSecurityManager::GetSecurityContext – metoda</span><span class="sxs-lookup"><span data-stu-id="17e0d-102">IHostSecurityManager::GetSecurityContext Method</span></span>
<span data-ttu-id="17e0d-103">Získá požadované [ihostsecuritycontext –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) z hostitele.</span><span class="sxs-lookup"><span data-stu-id="17e0d-103">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17e0d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17e0d-104">Syntax</span></span>  
  
```  
HRESULT GetSecurityContext (  
    [in]  EContextType eContextType,   
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="17e0d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="17e0d-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="17e0d-106">[v] Jeden z [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) hodnoty, která určuje, jaký typ kontext zabezpečení, který má vrátit.</span><span class="sxs-lookup"><span data-stu-id="17e0d-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of security context to return.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="17e0d-107">[out] Na adresu ukazatele rozhraní na `IHostSecurityContext` z `eContextType`.</span><span class="sxs-lookup"><span data-stu-id="17e0d-107">[out] The address of an interface pointer to the `IHostSecurityContext` of `eContextType`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17e0d-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="17e0d-108">Return Value</span></span>  
  
|<span data-ttu-id="17e0d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="17e0d-109">HRESULT</span></span>|<span data-ttu-id="17e0d-110">Popis</span><span class="sxs-lookup"><span data-stu-id="17e0d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="17e0d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="17e0d-111">S_OK</span></span>|<span data-ttu-id="17e0d-112">`GetSecurityContext` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="17e0d-112">`GetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="17e0d-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="17e0d-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="17e0d-114">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="17e0d-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="17e0d-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="17e0d-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="17e0d-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="17e0d-116">The call timed out.</span></span>|  
|<span data-ttu-id="17e0d-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="17e0d-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="17e0d-118">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="17e0d-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="17e0d-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="17e0d-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="17e0d-120">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="17e0d-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="17e0d-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="17e0d-121">E_FAIL</span></span>|<span data-ttu-id="17e0d-122">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="17e0d-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="17e0d-123">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="17e0d-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="17e0d-124">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="17e0d-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17e0d-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="17e0d-125">Remarks</span></span>  
 <span data-ttu-id="17e0d-126">Hostitel můžou řídit všechny kódu přístup k vlákno tokeny kódem CLR i uživateli.</span><span class="sxs-lookup"><span data-stu-id="17e0d-126">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="17e0d-127">Ho můžete také zajistit, že dokončení zabezpečení informace o kontextu je předán přes asynchronních operací nebo body kódu s přístupem kód s omezeným přístupem.</span><span class="sxs-lookup"><span data-stu-id="17e0d-127">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="17e0d-128">`IHostSecurityContext` zapouzdří tato informace kontextu zabezpečení, která je plné krytí modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="17e0d-128">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span> <span data-ttu-id="17e0d-129">Modul CLR zaznamená tyto informace a přesouvá ji napříč vlákno fondu pracovní položka odesílání, provádění finalizační metodu a modul a třída konstrukce.</span><span class="sxs-lookup"><span data-stu-id="17e0d-129">The CLR captures this information and moves it across thread pool worker item dispatch, finalizer execution, and module and class construction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17e0d-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="17e0d-130">Requirements</span></span>  
 <span data-ttu-id="17e0d-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17e0d-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17e0d-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="17e0d-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="17e0d-133">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="17e0d-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="17e0d-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17e0d-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17e0d-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="17e0d-135">See Also</span></span>  
 [<span data-ttu-id="17e0d-136">EContextType – výčet</span><span class="sxs-lookup"><span data-stu-id="17e0d-136">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)  
 [<span data-ttu-id="17e0d-137">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="17e0d-137">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="17e0d-138">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="17e0d-138">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
