---
title: ICLRControl::SetAppDomainManagerType – metoda
ms.date: 03/30/2017
api_name:
- ICLRControl.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRControl interface [.NET Framework hosting]
- ICLRControl::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ec57828b-2aad-496d-a35a-e45d4bd7fe77
topic_type:
- apiref
ms.openlocfilehash: be29a4f83901b8e8fc338c2daa8f5703523402b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126579"
---
# <a name="iclrcontrolsetappdomainmanagertype-method"></a><span data-ttu-id="fe5c6-102">ICLRControl::SetAppDomainManagerType – metoda</span><span class="sxs-lookup"><span data-stu-id="fe5c6-102">ICLRControl::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="fe5c6-103">Nastaví typ odvozený od <xref:System.AppDomainManager> jako typ pro správce domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="fe5c6-103">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe5c6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe5c6-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManagerType (  
    [in] LPCWSTR pwzAppDomainManagerAssembly,  
    [in] LPCWSTR pwzAppDomainManagerType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe5c6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fe5c6-105">Parameters</span></span>  
 `pwzAppDomainManagerAssembly`  
 <span data-ttu-id="fe5c6-106">pro Název sestavení, ve kterém je implementován požadovaný typ odvozený od <xref:System.AppDomainManager>.</span><span class="sxs-lookup"><span data-stu-id="fe5c6-106">[in] The name of the assembly in which the requested type derived from <xref:System.AppDomainManager> is implemented.</span></span>  
  
 `pwzAppDomainManagerType`  
 <span data-ttu-id="fe5c6-107">pro Název typu implementovaného v parametru `pwzAppDomainManagerAssembly`, který implementuje možnosti <xref:System.AppDomainManager>.</span><span class="sxs-lookup"><span data-stu-id="fe5c6-107">[in] The name of the type implemented in the `pwzAppDomainManagerAssembly` parameter that implements the capabilities of <xref:System.AppDomainManager>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe5c6-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fe5c6-108">Return Value</span></span>  
  
|<span data-ttu-id="fe5c6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fe5c6-109">HRESULT</span></span>|<span data-ttu-id="fe5c6-110">Popis</span><span class="sxs-lookup"><span data-stu-id="fe5c6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fe5c6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="fe5c6-111">S_OK</span></span>|<span data-ttu-id="fe5c6-112">Metoda byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="fe5c6-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="fe5c6-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fe5c6-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fe5c6-114">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="fe5c6-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fe5c6-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fe5c6-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fe5c6-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="fe5c6-116">The call timed out.</span></span>|  
|<span data-ttu-id="fe5c6-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fe5c6-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fe5c6-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="fe5c6-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fe5c6-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fe5c6-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fe5c6-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="fe5c6-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fe5c6-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fe5c6-121">E_FAIL</span></span>|<span data-ttu-id="fe5c6-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="fe5c6-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fe5c6-123">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="fe5c6-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fe5c6-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fe5c6-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fe5c6-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fe5c6-125">Requirements</span></span>  
 <span data-ttu-id="fe5c6-126">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe5c6-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe5c6-127">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fe5c6-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fe5c6-128">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fe5c6-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fe5c6-129">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe5c6-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe5c6-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fe5c6-130">See also</span></span>

- [<span data-ttu-id="fe5c6-131">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fe5c6-131">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="fe5c6-132">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fe5c6-132">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
