---
title: "LockClrVersion – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- LockClrVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LockClrVersion
helpviewer_keywords:
- LockClrVersion function [.NET Framework hosting]
ms.assetid: 1318ee37-c43b-40eb-bbe8-88fc46453d74
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a58d7e99f545026f6f133901ef35a1f9b9fabc7d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="lockclrversion-function"></a><span data-ttu-id="742e5-102">LockClrVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="742e5-102">LockClrVersion Function</span></span>
<span data-ttu-id="742e5-103">Umožňuje na hostiteli a určit, která verze common language runtime (CLR) se použije v procesu před explicitně inicializace modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="742e5-103">Allows the host to determine which version of the common language runtime (CLR) will be used within the process before explicitly initializing the CLR.</span></span>  
  
 <span data-ttu-id="742e5-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="742e5-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="742e5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="742e5-105">Syntax</span></span>  
  
```  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="742e5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="742e5-106">Parameters</span></span>  
 `hostCallback`  
 <span data-ttu-id="742e5-107">[v] Funkce, která má být volána při inicializaci modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="742e5-107">[in] The function to be called by the CLR upon initialization.</span></span>  
  
 `pBeginHostSetup`  
 <span data-ttu-id="742e5-108">[v] Funkce, která má být voláno hostitelem k informování modulu CLR této inicializace se spouští.</span><span class="sxs-lookup"><span data-stu-id="742e5-108">[in] The function to be called by the host to inform the CLR that initialization is starting.</span></span>  
  
 `pEndHostSetup`  
 <span data-ttu-id="742e5-109">[v] Funkce, která má být voláno hostitelem k informování modulu CLR této inicializace je dokončena.</span><span class="sxs-lookup"><span data-stu-id="742e5-109">[in] The function to be called by the host to inform the CLR that initialization is complete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="742e5-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="742e5-110">Return Value</span></span>  
 <span data-ttu-id="742e5-111">Tato metoda vrátí standardní kódy chyb COM, jak jsou definovány v WinError.h, kromě následující hodnoty.</span><span class="sxs-lookup"><span data-stu-id="742e5-111">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="742e5-112">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="742e5-112">Return code</span></span>|<span data-ttu-id="742e5-113">Popis</span><span class="sxs-lookup"><span data-stu-id="742e5-113">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="742e5-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="742e5-114">S_OK</span></span>|<span data-ttu-id="742e5-115">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="742e5-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="742e5-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="742e5-116">E_INVALIDARG</span></span>|<span data-ttu-id="742e5-117">Jeden nebo více parametrů má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="742e5-117">One or more of the arguments is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="742e5-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="742e5-118">Remarks</span></span>  
 <span data-ttu-id="742e5-119">Volání hostitele `LockClrVersion` před inicializace modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="742e5-119">The host calls `LockClrVersion` before initializing the CLR.</span></span> <span data-ttu-id="742e5-120">`LockClrVersion`přijímá tři parametry, které jsou zpětná volání typu [FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md).</span><span class="sxs-lookup"><span data-stu-id="742e5-120">`LockClrVersion` takes three parameters, all of which are callbacks of type [FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md).</span></span> <span data-ttu-id="742e5-121">Tento typ je definován následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="742e5-121">This type is defined as follows.</span></span>  
  
```  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 <span data-ttu-id="742e5-122">Při inicializaci modulu runtime dojít k následující kroky:</span><span class="sxs-lookup"><span data-stu-id="742e5-122">The following steps occur upon initialization of the runtime:</span></span>  
  
1.  <span data-ttu-id="742e5-123">Volání hostitele [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) nebo jednoho z dalších funkcí inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="742e5-123">The host calls [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or one of the other runtime initialization functions.</span></span> <span data-ttu-id="742e5-124">Alternativně hostitele může provést inicializaci modulu runtime použijte aktivace objektu COM.</span><span class="sxs-lookup"><span data-stu-id="742e5-124">Alternatively, the host could initialize the runtime using COM object activation.</span></span>  
  
2.  <span data-ttu-id="742e5-125">Modul runtime volá funkci určeného `hostCallback` parametr.</span><span class="sxs-lookup"><span data-stu-id="742e5-125">The runtime calls the function specified by the `hostCallback` parameter.</span></span>  
  
3.  <span data-ttu-id="742e5-126">Funkce určeného `hostCallback` pak provede následující pořadí volání:</span><span class="sxs-lookup"><span data-stu-id="742e5-126">The function specified by `hostCallback` then makes the following sequence of calls:</span></span>  
  
    -   <span data-ttu-id="742e5-127">Funkce určeného `pBeginHostSetup` parametr.</span><span class="sxs-lookup"><span data-stu-id="742e5-127">The function specified by the `pBeginHostSetup` parameter.</span></span>  
  
    -   <span data-ttu-id="742e5-128">`CorBindToRuntimeEx`(nebo jinou funkci inicializace modulu runtime).</span><span class="sxs-lookup"><span data-stu-id="742e5-128">`CorBindToRuntimeEx` (or another runtime initialization function).</span></span>  
  
    -   <span data-ttu-id="742e5-129">[Iclrruntimehost::sethostcontrol –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).</span><span class="sxs-lookup"><span data-stu-id="742e5-129">[ICLRRuntimeHost::SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).</span></span>  
  
    -   <span data-ttu-id="742e5-130">[Iclrruntimehost::Start –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="742e5-130">[ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).</span></span>  
  
    -   <span data-ttu-id="742e5-131">Funkce určeného `pEndHostSetup` parametr.</span><span class="sxs-lookup"><span data-stu-id="742e5-131">The function specified by the `pEndHostSetup` parameter.</span></span>  
  
 <span data-ttu-id="742e5-132">Všechna volání z `pBeginHostSetup` k `pEndHostSetup` musí dojít k na jedno vlákno nebo fiber se stejným zásobníkem logické.</span><span class="sxs-lookup"><span data-stu-id="742e5-132">All the calls from `pBeginHostSetup` to `pEndHostSetup` must occur on a single thread or fiber, with the same logical stack.</span></span> <span data-ttu-id="742e5-133">Tento přístup z více vláken se může lišit od vlákno němž `hostCallback` je volána.</span><span class="sxs-lookup"><span data-stu-id="742e5-133">This thread can be different from the thread upon which `hostCallback` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="742e5-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="742e5-134">Requirements</span></span>  
 <span data-ttu-id="742e5-135">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="742e5-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="742e5-136">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="742e5-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="742e5-137">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="742e5-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="742e5-138">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="742e5-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="742e5-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="742e5-139">See Also</span></span>  
 [<span data-ttu-id="742e5-140">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="742e5-140">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
