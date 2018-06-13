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
ms.openlocfilehash: 96352ec5eaba67489dbef999925c56475611746c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435965"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="5c781-102">ICLRRuntimeHost::ExecuteInAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="5c781-102">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>
<span data-ttu-id="5c781-103">Určuje <xref:System.AppDomain> ve kterém se má provést zadanou spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="5c781-103">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c781-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c781-104">Syntax</span></span>  
  
```  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,   
    [in] FExecuteInDomainCallback pCallback,   
    [in] void* cookie  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5c781-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5c781-105">Parameters</span></span>  
 `AppDomainId`  
 <span data-ttu-id="5c781-106">[v] Číselné ID <xref:System.AppDomain> ve kterém se má provést zadanou metodu.</span><span class="sxs-lookup"><span data-stu-id="5c781-106">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="5c781-107">[v] Ukazatel na funkci provést v rámci zadaného <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="5c781-107">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="5c781-108">[v] Ukazatel na neprůhledné paměti přidělené volajícího.</span><span class="sxs-lookup"><span data-stu-id="5c781-108">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="5c781-109">Tento parametr je modul CLR (CLR) předaná funkci zpětného volání domény.</span><span class="sxs-lookup"><span data-stu-id="5c781-109">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="5c781-110">Není paměť haldy spravovaného modulu runtime; přidělení i životnost tuto paměť jsou řízeny volající.</span><span class="sxs-lookup"><span data-stu-id="5c781-110">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c781-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5c781-111">Return Value</span></span>  
  
|<span data-ttu-id="5c781-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5c781-112">HRESULT</span></span>|<span data-ttu-id="5c781-113">Popis</span><span class="sxs-lookup"><span data-stu-id="5c781-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5c781-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="5c781-114">S_OK</span></span>|<span data-ttu-id="5c781-115">`ExecuteInAppDomain` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="5c781-115">`ExecuteInAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="5c781-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5c781-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5c781-117">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="5c781-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5c781-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5c781-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5c781-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="5c781-119">The call timed out.</span></span>|  
|<span data-ttu-id="5c781-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5c781-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5c781-121">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="5c781-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5c781-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5c781-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5c781-123">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="5c781-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5c781-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5c781-124">E_FAIL</span></span>|<span data-ttu-id="5c781-125">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="5c781-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5c781-126">Pokud metoda vrátí E_FAIL, modul CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="5c781-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5c781-127">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5c781-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c781-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5c781-128">Remarks</span></span>  
 <span data-ttu-id="5c781-129">`ExecuteInAppDomain` Umožňuje kontrolu využití hostiteli over, který spravuje <xref:System.AppDomain> zadanou metodu spravované se má provést v.</span><span class="sxs-lookup"><span data-stu-id="5c781-129">`ExecuteInAppDomain` allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="5c781-130">Hodnota identifikátoru doménu aplikace, který odpovídá hodnotě můžete získat <xref:System.AppDomain.Id%2A> vlastnost voláním [getcurrentappdomainid – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="5c781-130">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c781-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5c781-131">Requirements</span></span>  
 <span data-ttu-id="5c781-132">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c781-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c781-133">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5c781-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5c781-134">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5c781-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c781-135">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c781-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c781-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="5c781-136">See Also</span></span>  
 [<span data-ttu-id="5c781-137">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5c781-137">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
