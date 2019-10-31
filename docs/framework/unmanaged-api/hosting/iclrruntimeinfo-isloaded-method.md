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
ms.openlocfilehash: e0ab16348abbaff00152f2b259ccafdd331174df
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136362"
---
# <a name="iclrruntimeinfoisloaded-method"></a><span data-ttu-id="eb895-102">ICLRRuntimeInfo::IsLoaded – metoda</span><span class="sxs-lookup"><span data-stu-id="eb895-102">ICLRRuntimeInfo::IsLoaded Method</span></span>
<span data-ttu-id="eb895-103">Označuje, zda je modul CLR (Common Language Runtime) přidružený k rozhraní [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="eb895-103">Indicates whether the common language runtime (CLR) associated with the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface is loaded into a process.</span></span> <span data-ttu-id="eb895-104">Modul runtime lze načíst bez nutnosti také spuštění.</span><span class="sxs-lookup"><span data-stu-id="eb895-104">A runtime can be loaded without also being started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb895-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb895-105">Syntax</span></span>  
  
```cpp  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb895-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="eb895-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="eb895-107">pro Popisovač procesu.</span><span class="sxs-lookup"><span data-stu-id="eb895-107">[in] A handle to the process.</span></span>  
  
 `pbLoaded`  
 <span data-ttu-id="eb895-108">[out] `true`, pokud je modul CLR načten do procesu; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="eb895-108">[out] `true` if the CLR is loaded into the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eb895-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="eb895-109">Return Value</span></span>  
 <span data-ttu-id="eb895-110">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="eb895-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="eb895-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eb895-111">HRESULT</span></span>|<span data-ttu-id="eb895-112">Popis</span><span class="sxs-lookup"><span data-stu-id="eb895-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eb895-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="eb895-113">S_OK</span></span>|<span data-ttu-id="eb895-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="eb895-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="eb895-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="eb895-115">E_POINTER</span></span>|<span data-ttu-id="eb895-116">`pbLoaded` je null.</span><span class="sxs-lookup"><span data-stu-id="eb895-116">`pbLoaded` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb895-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eb895-117">Remarks</span></span>  
 <span data-ttu-id="eb895-118">Tato metoda je zpětně kompatibilní s následujícími funkcemi a rozhraními:</span><span class="sxs-lookup"><span data-stu-id="eb895-118">This method is backward-compatible with the following functions and interfaces:</span></span>  
  
- <span data-ttu-id="eb895-119">Rozhraní [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) (v rozhraní API pro hostování .NET Framework verze 1).</span><span class="sxs-lookup"><span data-stu-id="eb895-119">[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface (in the .NET Framework version 1 hosting API).</span></span>  
  
- <span data-ttu-id="eb895-120">Rozhraní [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) (rozhraní API pro hostování .NET Framework 2,0).</span><span class="sxs-lookup"><span data-stu-id="eb895-120">[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface (in the .NET Framework 2.0 hosting API).</span></span>  
  
- <span data-ttu-id="eb895-121">Zastaralé funkce `CorBindTo*` (viz téma [zastaralé funkce hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) v rozhraní API pro hostování .NET Framework 2,0).</span><span class="sxs-lookup"><span data-stu-id="eb895-121">Deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span>  
  
 <span data-ttu-id="eb895-122">Hostitel může zavolat jednu z zastaralých funkcí `CorBindTo*`, jako je například funkce [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) , pro vytvoření instance konkrétní verze modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="eb895-122">A host may call one of the deprecated `CorBindTo*` functions, such as the [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) function, to instantiate a specific version of the CLR.</span></span> <span data-ttu-id="eb895-123">Hostitel pak může zavolat metodu [ICLRMetaHost:: GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) a zadat stejné číslo verze pro získání rozhraní [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="eb895-123">The host could then call the [ICLRMetaHost::GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) method and specify the same version number to obtain a [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="eb895-124">Pokud hostitel pak zavolá metodu `IsLoaded` v vráceném rozhraní [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) , `pbLoaded` vrátí `true`; v opačném případě vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="eb895-124">If the host then calls the `IsLoaded` method on the returned [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, `pbLoaded` returns `true`; otherwise, it returns `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb895-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eb895-125">Requirements</span></span>  
 <span data-ttu-id="eb895-126">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb895-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb895-127">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="eb895-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="eb895-128">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="eb895-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eb895-129">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb895-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb895-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eb895-130">See also</span></span>

- [<span data-ttu-id="eb895-131">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eb895-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="eb895-132">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="eb895-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="eb895-133">Hostování</span><span class="sxs-lookup"><span data-stu-id="eb895-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
