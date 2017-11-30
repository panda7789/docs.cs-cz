---
title: "ICLRMetaHost::RequestRuntimeLoadedNotification – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.RequestRuntimeLoadedNotification
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::RequestRuntimeLoadedNotification
helpviewer_keywords:
- RequestRuntimeLoadedNotification method [.NET Framework hosting]
- ICLRMetaHost::RequestRuntimeLoadedNotification method [.NET Framework hosting]
ms.assetid: 0d5ccc4d-0193-41f5-af54-45d7b70d5321
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 32eb92263685bc3be9f0c28dea88ecfa78c2b52c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a><span data-ttu-id="9ee38-102">ICLRMetaHost::RequestRuntimeLoadedNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="9ee38-102">ICLRMetaHost::RequestRuntimeLoadedNotification Method</span></span>
<span data-ttu-id="9ee38-103">Poskytuje funkci zpětného volání, která záruku, která se má volat při společné jazykové verzi modulu runtime (CLR) je prvním načtení, ale ještě nebyla spuštěna.</span><span class="sxs-lookup"><span data-stu-id="9ee38-103">Provides a callback function that is guaranteed to be called when a common language runtime (CLR) version is first loaded, but not yet started.</span></span> <span data-ttu-id="9ee38-104">Tato metoda nahrazuje [lockclrversion –](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="9ee38-104">This method supersedes the [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ee38-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ee38-105">Syntax</span></span>  
  
```  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9ee38-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9ee38-106">Parameters</span></span>  
 `pCallbackFunction`  
 <span data-ttu-id="9ee38-107">[v] Funkce zpětného volání, která je volána, když se načetl nový modul runtime.</span><span class="sxs-lookup"><span data-stu-id="9ee38-107">[in] The callback function that is invoked when a new runtime has been loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ee38-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9ee38-108">Return Value</span></span>  
 <span data-ttu-id="9ee38-109">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="9ee38-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9ee38-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9ee38-110">HRESULT</span></span>|<span data-ttu-id="9ee38-111">Popis</span><span class="sxs-lookup"><span data-stu-id="9ee38-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9ee38-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="9ee38-112">S_OK</span></span>|<span data-ttu-id="9ee38-113">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="9ee38-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="9ee38-114">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="9ee38-114">E_POINTER</span></span>|<span data-ttu-id="9ee38-115">`pCallbackFunction`má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="9ee38-115">`pCallbackFunction` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ee38-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9ee38-116">Remarks</span></span>  
 <span data-ttu-id="9ee38-117">Zpětné volání funguje následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="9ee38-117">The callback works in the following way:</span></span>  
  
-   <span data-ttu-id="9ee38-118">Zpětné volání je volána, pouze v případě, že je první načíst modul runtime.</span><span class="sxs-lookup"><span data-stu-id="9ee38-118">The callback is invoked only when a runtime is loaded for the first time.</span></span>  
  
-   <span data-ttu-id="9ee38-119">Zpětné volání není volána pro vícenásobné zátěže stejné modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="9ee38-119">The callback is not invoked for reentrant loads of the same runtime.</span></span>  
  
-   <span data-ttu-id="9ee38-120">Pro modul runtime nejsou vícenásobně přístupné zátěže se serializují volání funkce zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="9ee38-120">For non-reentrant runtime loads, calls to the callback function are serialized.</span></span>  
  
 <span data-ttu-id="9ee38-121">Funkce zpětného volání má následující prototyp:</span><span class="sxs-lookup"><span data-stu-id="9ee38-121">The callback function has the following prototype:</span></span>  
  
```  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 <span data-ttu-id="9ee38-122">Prototypy funkcí zpětného volání jsou následující:</span><span class="sxs-lookup"><span data-stu-id="9ee38-122">The callback function prototypes are as follows:</span></span>  
  
-   <span data-ttu-id="9ee38-123">`pfnCallbackThreadSet`:</span><span class="sxs-lookup"><span data-stu-id="9ee38-123">`pfnCallbackThreadSet`:</span></span>  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
-   <span data-ttu-id="9ee38-124">`pfnCallbackThreadUnset`:</span><span class="sxs-lookup"><span data-stu-id="9ee38-124">`pfnCallbackThreadUnset`:</span></span>  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 <span data-ttu-id="9ee38-125">Pokud hostitel chtít načíst nebo způsobit jiný modul runtime načíst vícenásobné způsobem `pfnCallbackThreadSet` a `pfnCallbackThreadUnset` parametry, které jsou k dispozici v zpětné volání funkce použije následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="9ee38-125">If the host intends to load or cause another runtime to be loaded in a reentrant manner, the `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` parameters that are provided in the callback function must be used in the following way:</span></span>  
  
-   <span data-ttu-id="9ee38-126">`pfnCallbackThreadSet`musí být voláno vlákno, které může způsobit runtime zatížení předtím, než dojde k pokusu o takové zatížení.</span><span class="sxs-lookup"><span data-stu-id="9ee38-126">`pfnCallbackThreadSet` must be called by the thread that might cause a runtime load before such a load is attempted.</span></span>  
  
-   <span data-ttu-id="9ee38-127">`pfnCallbackThreadUnset`musí být volána, když vlákno už způsobí zatížení runtime (a před návratem od počáteční zpětné volání).</span><span class="sxs-lookup"><span data-stu-id="9ee38-127">`pfnCallbackThreadUnset` must be called when the thread will no longer cause such a runtime load (and before returning from the initial callback).</span></span>  
  
-   <span data-ttu-id="9ee38-128">`pfnCallbackThreadSet`a `pfnCallbackThreadUnset` jsou obě nejsou vícenásobně přístupné.</span><span class="sxs-lookup"><span data-stu-id="9ee38-128">`pfnCallbackThreadSet` and `pfnCallbackThreadUnset` are both non-reentrant.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ee38-129">Hostování aplikací nesmějí provádět volání `pfnCallbackThreadSet` a `pfnCallbackThreadUnset` mimo obor `pCallbackFunction` parametr.</span><span class="sxs-lookup"><span data-stu-id="9ee38-129">Host applications must not call `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` outside the scope of the `pCallbackFunction` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ee38-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9ee38-130">Requirements</span></span>  
 <span data-ttu-id="9ee38-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ee38-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ee38-132">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="9ee38-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9ee38-133">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9ee38-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ee38-134">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ee38-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ee38-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="9ee38-135">See Also</span></span>  
 [<span data-ttu-id="9ee38-136">Iclrmetahost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9ee38-136">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="9ee38-137">Hostování</span><span class="sxs-lookup"><span data-stu-id="9ee38-137">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
