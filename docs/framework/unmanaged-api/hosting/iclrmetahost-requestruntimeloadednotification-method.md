---
title: ICLRMetaHost::RequestRuntimeLoadedNotification – metoda
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::RequestRuntimeLoadedNotification
helpviewer_keywords:
- RequestRuntimeLoadedNotification method [.NET Framework hosting]
- ICLRMetaHost::RequestRuntimeLoadedNotification method [.NET Framework hosting]
ms.assetid: 0d5ccc4d-0193-41f5-af54-45d7b70d5321
topic_type:
- apiref
ms.openlocfilehash: 23f868bba2dc058d99f1c5c09e9b311b1ff3634a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140901"
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a><span data-ttu-id="4b0bc-102">ICLRMetaHost::RequestRuntimeLoadedNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="4b0bc-102">ICLRMetaHost::RequestRuntimeLoadedNotification Method</span></span>
<span data-ttu-id="4b0bc-103">Poskytuje funkci zpětného volání, která je zaručena k volání při prvním načtení verze modulu CLR (Common Language Runtime), ale ještě nebyla spuštěna.</span><span class="sxs-lookup"><span data-stu-id="4b0bc-103">Provides a callback function that is guaranteed to be called when a common language runtime (CLR) version is first loaded, but not yet started.</span></span> <span data-ttu-id="4b0bc-104">Tato metoda nahrazuje funkci [LockClrVersion –](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) .</span><span class="sxs-lookup"><span data-stu-id="4b0bc-104">This method supersedes the [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b0bc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b0bc-105">Syntax</span></span>  
  
```cpp  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b0bc-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4b0bc-106">Parameters</span></span>  
 `pCallbackFunction`  
 <span data-ttu-id="4b0bc-107">pro Funkce zpětného volání, která je vyvolána, když byl načten nový modul runtime.</span><span class="sxs-lookup"><span data-stu-id="4b0bc-107">[in] The callback function that is invoked when a new runtime has been loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4b0bc-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4b0bc-108">Return Value</span></span>  
 <span data-ttu-id="4b0bc-109">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="4b0bc-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4b0bc-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4b0bc-110">HRESULT</span></span>|<span data-ttu-id="4b0bc-111">Popis</span><span class="sxs-lookup"><span data-stu-id="4b0bc-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4b0bc-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="4b0bc-112">S_OK</span></span>|<span data-ttu-id="4b0bc-113">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="4b0bc-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="4b0bc-114">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="4b0bc-114">E_POINTER</span></span>|<span data-ttu-id="4b0bc-115">`pCallbackFunction` je null.</span><span class="sxs-lookup"><span data-stu-id="4b0bc-115">`pCallbackFunction` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b0bc-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4b0bc-116">Remarks</span></span>  
 <span data-ttu-id="4b0bc-117">Zpětné volání funguje následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="4b0bc-117">The callback works in the following way:</span></span>  
  
- <span data-ttu-id="4b0bc-118">Zpětné volání je vyvoláno pouze při prvním načtení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="4b0bc-118">The callback is invoked only when a runtime is loaded for the first time.</span></span>  
  
- <span data-ttu-id="4b0bc-119">Zpětné volání není vyvoláno pro znovu vstupující načtení stejného modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="4b0bc-119">The callback is not invoked for reentrant loads of the same runtime.</span></span>  
  
- <span data-ttu-id="4b0bc-120">Pro neopětovné zařazení za běhu jsou volání funkce zpětného volání serializována.</span><span class="sxs-lookup"><span data-stu-id="4b0bc-120">For non-reentrant runtime loads, calls to the callback function are serialized.</span></span>  
  
 <span data-ttu-id="4b0bc-121">Funkce zpětného volání má následující prototyp:</span><span class="sxs-lookup"><span data-stu-id="4b0bc-121">The callback function has the following prototype:</span></span>  
  
```cpp  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 <span data-ttu-id="4b0bc-122">Prototypy funkce zpětného volání jsou následující:</span><span class="sxs-lookup"><span data-stu-id="4b0bc-122">The callback function prototypes are as follows:</span></span>  
  
- <span data-ttu-id="4b0bc-123">`pfnCallbackThreadSet`:</span><span class="sxs-lookup"><span data-stu-id="4b0bc-123">`pfnCallbackThreadSet`:</span></span>  
  
    ```cpp  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
- <span data-ttu-id="4b0bc-124">`pfnCallbackThreadUnset`:</span><span class="sxs-lookup"><span data-stu-id="4b0bc-124">`pfnCallbackThreadUnset`:</span></span>  
  
    ```cpp  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 <span data-ttu-id="4b0bc-125">Pokud hostitel zamýšlí načíst nebo způsobí, že jiný modul runtime bude načten znovu, je nutné použít parametry `pfnCallbackThreadSet` a `pfnCallbackThreadUnset`, které jsou k dispozici ve funkci zpětného volání následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="4b0bc-125">If the host intends to load or cause another runtime to be loaded in a reentrant manner, the `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` parameters that are provided in the callback function must be used in the following way:</span></span>  
  
- <span data-ttu-id="4b0bc-126">`pfnCallbackThreadSet` musí být voláno vláknem, které může způsobit zatížení za běhu před tím, než se provede pokus o načtení.</span><span class="sxs-lookup"><span data-stu-id="4b0bc-126">`pfnCallbackThreadSet` must be called by the thread that might cause a runtime load before such a load is attempted.</span></span>  
  
- <span data-ttu-id="4b0bc-127">`pfnCallbackThreadUnset` musí být volána, pokud vlákno již nebude způsobovat takové načtení za běhu (a před návratem z prvotního zpětného volání).</span><span class="sxs-lookup"><span data-stu-id="4b0bc-127">`pfnCallbackThreadUnset` must be called when the thread will no longer cause such a runtime load (and before returning from the initial callback).</span></span>  
  
- <span data-ttu-id="4b0bc-128">`pfnCallbackThreadSet` a `pfnCallbackThreadUnset` se nepoužívají.</span><span class="sxs-lookup"><span data-stu-id="4b0bc-128">`pfnCallbackThreadSet` and `pfnCallbackThreadUnset` are both non-reentrant.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4b0bc-129">Hostitelské aplikace nesmí volat `pfnCallbackThreadSet` a `pfnCallbackThreadUnset` mimo obor parametru `pCallbackFunction`.</span><span class="sxs-lookup"><span data-stu-id="4b0bc-129">Host applications must not call `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` outside the scope of the `pCallbackFunction` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b0bc-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4b0bc-130">Requirements</span></span>  
 <span data-ttu-id="4b0bc-131">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b0bc-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b0bc-132">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="4b0bc-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4b0bc-133">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4b0bc-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4b0bc-134">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b0bc-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b0bc-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4b0bc-135">See also</span></span>

- [<span data-ttu-id="4b0bc-136">ICLRMetaHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4b0bc-136">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="4b0bc-137">Hostování</span><span class="sxs-lookup"><span data-stu-id="4b0bc-137">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
