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
ms.openlocfilehash: fd1d97d9f3a44e2237cfc7a9e054a5ecfa2ebb01
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57470754"
---
# <a name="iclrruntimeinfoisloaded-method"></a><span data-ttu-id="7d31d-102">ICLRRuntimeInfo::IsLoaded – metoda</span><span class="sxs-lookup"><span data-stu-id="7d31d-102">ICLRRuntimeInfo::IsLoaded Method</span></span>
<span data-ttu-id="7d31d-103">Určuje, zda modul CLR (CLR) přidružené k [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní je načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="7d31d-103">Indicates whether the common language runtime (CLR) associated with the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface is loaded into a process.</span></span> <span data-ttu-id="7d31d-104">Modul runtime je možné načíst bez také spuštění.</span><span class="sxs-lookup"><span data-stu-id="7d31d-104">A runtime can be loaded without also being started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d31d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d31d-105">Syntax</span></span>  
  
```  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d31d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d31d-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="7d31d-107">[in] Popisovač procesu.</span><span class="sxs-lookup"><span data-stu-id="7d31d-107">[in] A handle to the process.</span></span>  
  
 `pbLoaded`  
 <span data-ttu-id="7d31d-108">[out] `true` Pokud CLR je načten do procesu; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="7d31d-108">[out] `true` if the CLR is loaded into the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d31d-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7d31d-109">Return Value</span></span>  
 <span data-ttu-id="7d31d-110">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="7d31d-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7d31d-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7d31d-111">HRESULT</span></span>|<span data-ttu-id="7d31d-112">Popis</span><span class="sxs-lookup"><span data-stu-id="7d31d-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7d31d-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="7d31d-113">S_OK</span></span>|<span data-ttu-id="7d31d-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="7d31d-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="7d31d-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="7d31d-115">E_POINTER</span></span>|<span data-ttu-id="7d31d-116">`pbLoaded` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="7d31d-116">`pbLoaded` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d31d-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d31d-117">Remarks</span></span>  
 <span data-ttu-id="7d31d-118">Tato metoda je zpětně kompatibilní s následující funkce a rozhraní:</span><span class="sxs-lookup"><span data-stu-id="7d31d-118">This method is backward-compatible with the following functions and interfaces:</span></span>  
  
-   <span data-ttu-id="7d31d-119">[Icorruntimehost –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) rozhraní (v rozhraní .NET Framework verze 1 hostujícího rozhraní API).</span><span class="sxs-lookup"><span data-stu-id="7d31d-119">[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface (in the .NET Framework version 1 hosting API).</span></span>  
  
-   <span data-ttu-id="7d31d-120">[Iclrruntimehost –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) rozhraní (v rozhraní .NET Framework 2.0 hostování rozhraní API).</span><span class="sxs-lookup"><span data-stu-id="7d31d-120">[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface (in the .NET Framework 2.0 hosting API).</span></span>  
  
-   <span data-ttu-id="7d31d-121">Zastaralé `CorBindTo*` funkcí (viz [zastaralé funkce hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) v rozhraní .NET Framework 2.0, který je hostitelem rozhraní API).</span><span class="sxs-lookup"><span data-stu-id="7d31d-121">Deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span>  
  
 <span data-ttu-id="7d31d-122">Hostitel může volat jeden z zastaralá `CorBindTo*` funkce, jako [corbindtoruntime –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) funkce k vytvoření instance konkrétní verzi modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="7d31d-122">A host may call one of the deprecated `CorBindTo*` functions, such as the [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) function, to instantiate a specific version of the CLR.</span></span> <span data-ttu-id="7d31d-123">Hostitel pak lze volat [iclrmetahost::getruntime –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) – metoda a zadejte číslo verze získání [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7d31d-123">The host could then call the [ICLRMetaHost::GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) method and specify the same version number to obtain a [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="7d31d-124">Hostitel pak volá-li `IsLoaded` metodu na vrácený [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní, `pbLoaded` vrátí `true`; v opačném případě vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="7d31d-124">If the host then calls the `IsLoaded` method on the returned [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, `pbLoaded` returns `true`; otherwise, it returns `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d31d-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d31d-125">Requirements</span></span>  
 <span data-ttu-id="7d31d-126">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d31d-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d31d-127">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="7d31d-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7d31d-128">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7d31d-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d31d-129">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d31d-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d31d-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d31d-130">See also</span></span>
- [<span data-ttu-id="7d31d-131">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7d31d-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="7d31d-132">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="7d31d-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="7d31d-133">Hostování</span><span class="sxs-lookup"><span data-stu-id="7d31d-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
