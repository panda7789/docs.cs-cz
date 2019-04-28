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
ms.openlocfilehash: 86348c35a023e22d10c4ad2e08f5cb1104b895a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61641408"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="ef944-102">ICLRRuntimeHost::ExecuteInAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="ef944-102">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>
<span data-ttu-id="ef944-103">Určuje, <xref:System.AppDomain> v, který se má spustit zadaný spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="ef944-103">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef944-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef944-104">Syntax</span></span>  
  
```  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,   
    [in] FExecuteInDomainCallback pCallback,   
    [in] void* cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef944-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ef944-105">Parameters</span></span>  
 `AppDomainId`  
 <span data-ttu-id="ef944-106">[in] Číselné ID <xref:System.AppDomain> ve kterém chcete provést zadanou metodu.</span><span class="sxs-lookup"><span data-stu-id="ef944-106">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="ef944-107">[in] Ukazatele na funkce pro spuštění v rámci zadaného <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="ef944-107">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="ef944-108">[in] Ukazatel na neprůhledné paměť přidělenou volajícímu.</span><span class="sxs-lookup"><span data-stu-id="ef944-108">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="ef944-109">Tento parametr je předáván modulem common language runtime (CLR) pro zpětné volání domény.</span><span class="sxs-lookup"><span data-stu-id="ef944-109">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="ef944-110">Není runtime spravované haldy paměti. přidělování a životnosti tato paměť se řídí volající.</span><span class="sxs-lookup"><span data-stu-id="ef944-110">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ef944-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ef944-111">Return Value</span></span>  
  
|<span data-ttu-id="ef944-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ef944-112">HRESULT</span></span>|<span data-ttu-id="ef944-113">Popis</span><span class="sxs-lookup"><span data-stu-id="ef944-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ef944-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="ef944-114">S_OK</span></span>|<span data-ttu-id="ef944-115">`ExecuteInAppDomain` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="ef944-115">`ExecuteInAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="ef944-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ef944-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ef944-117">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="ef944-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ef944-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ef944-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ef944-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="ef944-119">The call timed out.</span></span>|  
|<span data-ttu-id="ef944-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ef944-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ef944-121">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="ef944-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ef944-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ef944-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ef944-123">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="ef944-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ef944-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ef944-124">E_FAIL</span></span>|<span data-ttu-id="ef944-125">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="ef944-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ef944-126">Pokud metoda vrátí E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="ef944-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ef944-127">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ef944-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef944-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ef944-128">Remarks</span></span>  
 <span data-ttu-id="ef944-129">`ExecuteInAppDomain` umožňuje hostiteli pro kontrolu využití selhání, který spravuje <xref:System.AppDomain> zadané spravované metody by měly být provedeny v.</span><span class="sxs-lookup"><span data-stu-id="ef944-129">`ExecuteInAppDomain` allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="ef944-130">Hodnota identifikátoru doménu aplikace, která odpovídá hodnotě lze získat <xref:System.AppDomain.Id%2A> vlastnost voláním [getcurrentappdomainid – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="ef944-130">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef944-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ef944-131">Requirements</span></span>  
 <span data-ttu-id="ef944-132">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef944-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef944-133">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ef944-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ef944-134">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ef944-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ef944-135">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef944-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef944-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ef944-136">See also</span></span>

- [<span data-ttu-id="ef944-137">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ef944-137">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
