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
ms.openlocfilehash: 7198698edce48546c4f9a82ace18d5a6e71891ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176250"
---
# <a name="ihostsecuritymanagergetsecuritycontext-method"></a><span data-ttu-id="626f8-102">IHostSecurityManager::GetSecurityContext – metoda</span><span class="sxs-lookup"><span data-stu-id="626f8-102">IHostSecurityManager::GetSecurityContext Method</span></span>
<span data-ttu-id="626f8-103">Získá požadované [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) z hostitele.</span><span class="sxs-lookup"><span data-stu-id="626f8-103">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="626f8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="626f8-104">Syntax</span></span>  
  
```cpp
HRESULT GetSecurityContext (  
    [in]  EContextType eContextType,
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="626f8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="626f8-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="626f8-106">[v] Jedna z hodnot [EContextType,](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) označující, jaký typ kontextu zabezpečení vrátit.</span><span class="sxs-lookup"><span data-stu-id="626f8-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of security context to return.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="626f8-107">[out] Adresa ukazatele rozhraní na `IHostSecurityContext` rozhraní `eContextType`.</span><span class="sxs-lookup"><span data-stu-id="626f8-107">[out] The address of an interface pointer to the `IHostSecurityContext` of `eContextType`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="626f8-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="626f8-108">Return Value</span></span>  
  
|<span data-ttu-id="626f8-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="626f8-109">HRESULT</span></span>|<span data-ttu-id="626f8-110">Popis</span><span class="sxs-lookup"><span data-stu-id="626f8-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="626f8-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="626f8-111">S_OK</span></span>|<span data-ttu-id="626f8-112">`GetSecurityContext`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="626f8-112">`GetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="626f8-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="626f8-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="626f8-114">Běžný jazyk runtime (CLR) nebyl načten do procesu nebo CLR je ve stavu, ve kterém nelze spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="626f8-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="626f8-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="626f8-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="626f8-116">Časový čas hovoru byl vypován.</span><span class="sxs-lookup"><span data-stu-id="626f8-116">The call timed out.</span></span>|  
|<span data-ttu-id="626f8-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="626f8-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="626f8-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="626f8-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="626f8-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="626f8-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="626f8-120">Událost byla zrušena, zatímco na ní čekalo blokované vlákno nebo vlákno.</span><span class="sxs-lookup"><span data-stu-id="626f8-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="626f8-121">E_fail</span><span class="sxs-lookup"><span data-stu-id="626f8-121">E_FAIL</span></span>|<span data-ttu-id="626f8-122">Došlo k neznámému katastrofickému selhání.</span><span class="sxs-lookup"><span data-stu-id="626f8-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="626f8-123">Když metoda vrátí E_FAIL CLR již není použitelný v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="626f8-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="626f8-124">Následná volání metod hostování vrátí HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="626f8-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="626f8-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="626f8-125">Remarks</span></span>  
 <span data-ttu-id="626f8-126">Hostitel může řídit přístup k veškerému kódu tokenů podprocesů podle clr a uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="626f8-126">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="626f8-127">Může také zajistit, že úplné informace o kontextu zabezpečení jsou předávány přes asynchronní operace nebo body kódu s omezeným přístupem kódu.</span><span class="sxs-lookup"><span data-stu-id="626f8-127">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="626f8-128">`IHostSecurityContext`zapouzdřuje tyto informace o kontextu zabezpečení, které jsou pro CLR neprůhledné.</span><span class="sxs-lookup"><span data-stu-id="626f8-128">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span> <span data-ttu-id="626f8-129">CLR zachytí tyto informace a přesune je přes odeslání pracovní položky fondu vláken, provádění finalizační metody a konstrukce modulu a třídy.</span><span class="sxs-lookup"><span data-stu-id="626f8-129">The CLR captures this information and moves it across thread pool worker item dispatch, finalizer execution, and module and class construction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="626f8-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="626f8-130">Requirements</span></span>  
 <span data-ttu-id="626f8-131">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="626f8-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="626f8-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="626f8-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="626f8-133">**Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="626f8-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="626f8-134">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="626f8-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="626f8-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="626f8-135">See also</span></span>

- [<span data-ttu-id="626f8-136">EContextType – výčet</span><span class="sxs-lookup"><span data-stu-id="626f8-136">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)
- [<span data-ttu-id="626f8-137">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="626f8-137">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="626f8-138">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="626f8-138">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
