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
ms.openlocfilehash: 3275a69683a312340f35841815685066def10b23
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762523"
---
# <a name="iclrruntimeinfoisloaded-method"></a><span data-ttu-id="21860-102">ICLRRuntimeInfo::IsLoaded – metoda</span><span class="sxs-lookup"><span data-stu-id="21860-102">ICLRRuntimeInfo::IsLoaded Method</span></span>
<span data-ttu-id="21860-103">Označuje, zda je modul CLR (Common Language Runtime) přidružený k rozhraní [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="21860-103">Indicates whether the common language runtime (CLR) associated with the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface is loaded into a process.</span></span> <span data-ttu-id="21860-104">Modul runtime lze načíst bez nutnosti také spuštění.</span><span class="sxs-lookup"><span data-stu-id="21860-104">A runtime can be loaded without also being started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21860-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21860-105">Syntax</span></span>  
  
```cpp  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21860-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="21860-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="21860-107">pro Popisovač procesu.</span><span class="sxs-lookup"><span data-stu-id="21860-107">[in] A handle to the process.</span></span>  
  
 `pbLoaded`  
 <span data-ttu-id="21860-108">[out] `true` Pokud je modul CLR načten do procesu; v opačném případě `false` .</span><span class="sxs-lookup"><span data-stu-id="21860-108">[out] `true` if the CLR is loaded into the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21860-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="21860-109">Return Value</span></span>  
 <span data-ttu-id="21860-110">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="21860-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="21860-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="21860-111">HRESULT</span></span>|<span data-ttu-id="21860-112">Popis</span><span class="sxs-lookup"><span data-stu-id="21860-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="21860-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="21860-113">S_OK</span></span>|<span data-ttu-id="21860-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="21860-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="21860-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="21860-115">E_POINTER</span></span>|<span data-ttu-id="21860-116">`pbLoaded`má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="21860-116">`pbLoaded` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21860-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="21860-117">Remarks</span></span>  
 <span data-ttu-id="21860-118">Tato metoda je zpětně kompatibilní s následujícími funkcemi a rozhraními:</span><span class="sxs-lookup"><span data-stu-id="21860-118">This method is backward-compatible with the following functions and interfaces:</span></span>  
  
- <span data-ttu-id="21860-119">Rozhraní [ICorRuntimeHost](icorruntimehost-interface.md) (v rozhraní API pro hostování .NET Framework verze 1).</span><span class="sxs-lookup"><span data-stu-id="21860-119">[ICorRuntimeHost](icorruntimehost-interface.md) interface (in the .NET Framework version 1 hosting API).</span></span>  
  
- <span data-ttu-id="21860-120">Rozhraní [ICLRRuntimeHost](iclrruntimehost-interface.md) (rozhraní API pro hostování .NET Framework 2,0).</span><span class="sxs-lookup"><span data-stu-id="21860-120">[ICLRRuntimeHost](iclrruntimehost-interface.md) interface (in the .NET Framework 2.0 hosting API).</span></span>  
  
- <span data-ttu-id="21860-121">Zastaralé `CorBindTo*` funkce (viz téma [zastaralé funkce hostování CLR](deprecated-clr-hosting-functions.md) v rozhraní API pro hostování .NET Framework 2,0).</span><span class="sxs-lookup"><span data-stu-id="21860-121">Deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span>  
  
 <span data-ttu-id="21860-122">Hostitel může zavolat jednu z zastaralých `CorBindTo*` funkcí, jako je například funkce [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) , pro vytvoření instance konkrétní verze modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="21860-122">A host may call one of the deprecated `CorBindTo*` functions, such as the [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) function, to instantiate a specific version of the CLR.</span></span> <span data-ttu-id="21860-123">Hostitel pak může zavolat metodu [ICLRMetaHost:: GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) a zadat stejné číslo verze pro získání rozhraní [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="21860-123">The host could then call the [ICLRMetaHost::GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) method and specify the same version number to obtain a [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="21860-124">Pokud hostitel pak zavolá `IsLoaded` metodu v vráceném rozhraní [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , `pbLoaded` vrátí hodnotu `true` . jinak vrátí `false` .</span><span class="sxs-lookup"><span data-stu-id="21860-124">If the host then calls the `IsLoaded` method on the returned [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface, `pbLoaded` returns `true`; otherwise, it returns `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21860-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="21860-125">Requirements</span></span>  
 <span data-ttu-id="21860-126">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21860-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21860-127">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="21860-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="21860-128">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="21860-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21860-129">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21860-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21860-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="21860-130">See also</span></span>

- [<span data-ttu-id="21860-131">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="21860-131">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="21860-132">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="21860-132">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="21860-133">Hostování</span><span class="sxs-lookup"><span data-stu-id="21860-133">Hosting</span></span>](index.md)
