---
title: ICLRRuntimeHost::ExecuteInAppDomain – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain method [.NET Framework hosting]
- ExecuteInAppDomain method [.NET Framework hosting]
ms.assetid: e2b0e2db-3fae-4b56-844e-d30a125a660c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 314ffb143e99f9490bcd4a6489f2afed314b7c2c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768757"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="2b444-102">ICLRRuntimeHost::ExecuteInAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="2b444-102">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>
<span data-ttu-id="2b444-103">Určuje, <xref:System.AppDomain> v, který se má spustit zadaný spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="2b444-103">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b444-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b444-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,   
    [in] FExecuteInDomainCallback pCallback,   
    [in] void* cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b444-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2b444-105">Parameters</span></span>  
 `AppDomainId`  
 <span data-ttu-id="2b444-106">[in] Číselné ID <xref:System.AppDomain> ve kterém chcete provést zadanou metodu.</span><span class="sxs-lookup"><span data-stu-id="2b444-106">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="2b444-107">[in] Ukazatele na funkce pro spuštění v rámci zadaného <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="2b444-107">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="2b444-108">[in] Ukazatel na neprůhledné paměť přidělenou volajícímu.</span><span class="sxs-lookup"><span data-stu-id="2b444-108">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="2b444-109">Tento parametr je předáván modulem common language runtime (CLR) pro zpětné volání domény.</span><span class="sxs-lookup"><span data-stu-id="2b444-109">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="2b444-110">Není runtime spravované haldy paměti. přidělování a životnosti tato paměť se řídí volající.</span><span class="sxs-lookup"><span data-stu-id="2b444-110">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b444-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2b444-111">Return Value</span></span>  
  
|<span data-ttu-id="2b444-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2b444-112">HRESULT</span></span>|<span data-ttu-id="2b444-113">Popis</span><span class="sxs-lookup"><span data-stu-id="2b444-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2b444-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="2b444-114">S_OK</span></span>|<span data-ttu-id="2b444-115">`ExecuteInAppDomain` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="2b444-115">`ExecuteInAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="2b444-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2b444-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2b444-117">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="2b444-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2b444-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2b444-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2b444-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="2b444-119">The call timed out.</span></span>|  
|<span data-ttu-id="2b444-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2b444-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2b444-121">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="2b444-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2b444-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2b444-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2b444-123">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="2b444-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2b444-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2b444-124">E_FAIL</span></span>|<span data-ttu-id="2b444-125">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="2b444-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2b444-126">Pokud metoda vrátí E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="2b444-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2b444-127">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2b444-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b444-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2b444-128">Remarks</span></span>  
 <span data-ttu-id="2b444-129">`ExecuteInAppDomain` umožňuje hostiteli pro kontrolu využití selhání, který spravuje <xref:System.AppDomain> zadané spravované metody by měly být provedeny v.</span><span class="sxs-lookup"><span data-stu-id="2b444-129">`ExecuteInAppDomain` allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="2b444-130">Hodnota identifikátoru doménu aplikace, která odpovídá hodnotě lze získat <xref:System.AppDomain.Id%2A> vlastnost voláním [getcurrentappdomainid – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="2b444-130">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b444-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2b444-131">Requirements</span></span>  
 <span data-ttu-id="2b444-132">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b444-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b444-133">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2b444-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2b444-134">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2b444-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2b444-135">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b444-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b444-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b444-136">See also</span></span>

- [<span data-ttu-id="2b444-137">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2b444-137">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
