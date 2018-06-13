---
title: ICLRRuntimeInfo::IsLoaded – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoaded
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoaded
helpviewer_keywords:
- IsLoaded method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoaded method [.NET Framework hosting]
ms.assetid: fdc5a3a7-71ff-4025-99a1-59e4ee0bfe1b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ff1723cb481ee946e0c5c433009d3d6d7460cf5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434660"
---
# <a name="iclrruntimeinfoisloaded-method"></a><span data-ttu-id="a0126-102">ICLRRuntimeInfo::IsLoaded – metoda</span><span class="sxs-lookup"><span data-stu-id="a0126-102">ICLRRuntimeInfo::IsLoaded Method</span></span>
<span data-ttu-id="a0126-103">Určuje, zda modul CLR (CLR) přidružené [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní je načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="a0126-103">Indicates whether the common language runtime (CLR) associated with the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface is loaded into a process.</span></span> <span data-ttu-id="a0126-104">Modul runtime můžete načíst bez také spuštění.</span><span class="sxs-lookup"><span data-stu-id="a0126-104">A runtime can be loaded without also being started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0126-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0126-105">Syntax</span></span>  
  
```  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0126-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a0126-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="a0126-107">[v] Popisovač pro proces.</span><span class="sxs-lookup"><span data-stu-id="a0126-107">[in] A handle to the process.</span></span>  
  
 `pbLoaded`  
 <span data-ttu-id="a0126-108">[out] `true` Pokud modulu CLR je načíst do procesu, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="a0126-108">[out] `true` if the CLR is loaded into the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0126-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a0126-109">Return Value</span></span>  
 <span data-ttu-id="a0126-110">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="a0126-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a0126-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a0126-111">HRESULT</span></span>|<span data-ttu-id="a0126-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a0126-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a0126-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="a0126-113">S_OK</span></span>|<span data-ttu-id="a0126-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="a0126-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="a0126-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="a0126-115">E_POINTER</span></span>|<span data-ttu-id="a0126-116">`pbLoaded` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="a0126-116">`pbLoaded` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0126-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a0126-117">Remarks</span></span>  
 <span data-ttu-id="a0126-118">Tato metoda je zpětně kompatibilní s následující funkce a rozhraní:</span><span class="sxs-lookup"><span data-stu-id="a0126-118">This method is backward-compatible with the following functions and interfaces:</span></span>  
  
-   <span data-ttu-id="a0126-119">[Icorruntimehost –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) rozhraní (v rozhraní .NET Framework verze 1 hostování API).</span><span class="sxs-lookup"><span data-stu-id="a0126-119">[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface (in the .NET Framework version 1 hosting API).</span></span>  
  
-   <span data-ttu-id="a0126-120">[Iclrruntimehost –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) rozhraní (v rozhraní .NET Framework 2.0 hostující rozhraní API).</span><span class="sxs-lookup"><span data-stu-id="a0126-120">[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface (in the .NET Framework 2.0 hosting API).</span></span>  
  
-   <span data-ttu-id="a0126-121">Zastaralé `CorBindTo*` funkce (viz [zastaralé funkce hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) v rozhraní .NET Framework 2.0, který je hostitelem rozhraní API).</span><span class="sxs-lookup"><span data-stu-id="a0126-121">Deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span>  
  
 <span data-ttu-id="a0126-122">Hostitel může volání jednoho z zastaralé `CorBindTo*` funkce, jako [corbindtoruntime –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) funkce pro vytvoření instance na konkrétní verzi modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="a0126-122">A host may call one of the deprecated `CorBindTo*` functions, such as the [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) function, to instantiate a specific version of the CLR.</span></span> <span data-ttu-id="a0126-123">Potom může volat hostitele [iclrmetahost::getruntime –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) metoda a zadejte číslo verze získat [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a0126-123">The host could then call the [ICLRMetaHost::GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) method and specify the same version number to obtain a [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="a0126-124">Pokud hostitel pak zavolá `IsLoaded` metodu vrácených [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní, `pbLoaded` vrátí `true`, jinak vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="a0126-124">If the host then calls the `IsLoaded` method on the returned [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, `pbLoaded` returns `true`; otherwise, it returns `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0126-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a0126-125">Requirements</span></span>  
 <span data-ttu-id="a0126-126">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0126-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0126-127">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="a0126-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a0126-128">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a0126-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a0126-129">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0126-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0126-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0126-130">See Also</span></span>  
 [<span data-ttu-id="a0126-131">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a0126-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="a0126-132">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="a0126-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="a0126-133">Hostování</span><span class="sxs-lookup"><span data-stu-id="a0126-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
