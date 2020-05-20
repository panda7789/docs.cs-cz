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
ms.openlocfilehash: 6813f72f9d27aeff90f797a6ca9370b22e03e6f0
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703703"
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a><span data-ttu-id="0cdd9-102">ICLRMetaHost::RequestRuntimeLoadedNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="0cdd9-102">ICLRMetaHost::RequestRuntimeLoadedNotification Method</span></span>
<span data-ttu-id="0cdd9-103">Poskytuje funkci zpětného volání, která je zaručena k volání při prvním načtení verze modulu CLR (Common Language Runtime), ale ještě nebyla spuštěna.</span><span class="sxs-lookup"><span data-stu-id="0cdd9-103">Provides a callback function that is guaranteed to be called when a common language runtime (CLR) version is first loaded, but not yet started.</span></span> <span data-ttu-id="0cdd9-104">Tato metoda nahrazuje funkci [LockClrVersion –](lockclrversion-function.md) .</span><span class="sxs-lookup"><span data-stu-id="0cdd9-104">This method supersedes the [LockClrVersion](lockclrversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cdd9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0cdd9-105">Syntax</span></span>  
  
```cpp  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0cdd9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0cdd9-106">Parameters</span></span>  
 `pCallbackFunction`  
 <span data-ttu-id="0cdd9-107">pro Funkce zpětného volání, která je vyvolána, když byl načten nový modul runtime.</span><span class="sxs-lookup"><span data-stu-id="0cdd9-107">[in] The callback function that is invoked when a new runtime has been loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0cdd9-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0cdd9-108">Return Value</span></span>  
 <span data-ttu-id="0cdd9-109">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="0cdd9-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0cdd9-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0cdd9-110">HRESULT</span></span>|<span data-ttu-id="0cdd9-111">Popis</span><span class="sxs-lookup"><span data-stu-id="0cdd9-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0cdd9-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="0cdd9-112">S_OK</span></span>|<span data-ttu-id="0cdd9-113">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="0cdd9-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="0cdd9-114">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="0cdd9-114">E_POINTER</span></span>|<span data-ttu-id="0cdd9-115">`pCallbackFunction`má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="0cdd9-115">`pCallbackFunction` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0cdd9-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0cdd9-116">Remarks</span></span>  
 <span data-ttu-id="0cdd9-117">Zpětné volání funguje následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="0cdd9-117">The callback works in the following way:</span></span>  
  
- <span data-ttu-id="0cdd9-118">Zpětné volání je vyvoláno pouze při prvním načtení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="0cdd9-118">The callback is invoked only when a runtime is loaded for the first time.</span></span>  
  
- <span data-ttu-id="0cdd9-119">Zpětné volání není vyvoláno pro znovu vstupující načtení stejného modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="0cdd9-119">The callback is not invoked for reentrant loads of the same runtime.</span></span>  
  
- <span data-ttu-id="0cdd9-120">Pro neopětovné zařazení za běhu jsou volání funkce zpětného volání serializována.</span><span class="sxs-lookup"><span data-stu-id="0cdd9-120">For non-reentrant runtime loads, calls to the callback function are serialized.</span></span>  
  
 <span data-ttu-id="0cdd9-121">Funkce zpětného volání má následující prototyp:</span><span class="sxs-lookup"><span data-stu-id="0cdd9-121">The callback function has the following prototype:</span></span>  
  
```cpp  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 <span data-ttu-id="0cdd9-122">Prototypy funkce zpětného volání jsou následující:</span><span class="sxs-lookup"><span data-stu-id="0cdd9-122">The callback function prototypes are as follows:</span></span>  
  
- <span data-ttu-id="0cdd9-123">`pfnCallbackThreadSet`:</span><span class="sxs-lookup"><span data-stu-id="0cdd9-123">`pfnCallbackThreadSet`:</span></span>  
  
    ```cpp  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
- <span data-ttu-id="0cdd9-124">`pfnCallbackThreadUnset`:</span><span class="sxs-lookup"><span data-stu-id="0cdd9-124">`pfnCallbackThreadUnset`:</span></span>  
  
    ```cpp  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 <span data-ttu-id="0cdd9-125">Pokud hostitel zamýšlí načíst nebo způsobí, že jiný modul runtime bude načten znovu, `pfnCallbackThreadSet` `pfnCallbackThreadUnset` parametry a, které jsou zadány ve funkci zpětného volání, musí být použity následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="0cdd9-125">If the host intends to load or cause another runtime to be loaded in a reentrant manner, the `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` parameters that are provided in the callback function must be used in the following way:</span></span>  
  
- <span data-ttu-id="0cdd9-126">`pfnCallbackThreadSet`musí být voláno vláknem, které může způsobit načtení za běhu před tím, než se provede pokus o načtení.</span><span class="sxs-lookup"><span data-stu-id="0cdd9-126">`pfnCallbackThreadSet` must be called by the thread that might cause a runtime load before such a load is attempted.</span></span>  
  
- <span data-ttu-id="0cdd9-127">`pfnCallbackThreadUnset`musí být volána, pokud vlákno již nebude způsobovat takové načtení za běhu (a před návratem z prvotního zpětného volání).</span><span class="sxs-lookup"><span data-stu-id="0cdd9-127">`pfnCallbackThreadUnset` must be called when the thread will no longer cause such a runtime load (and before returning from the initial callback).</span></span>  
  
- <span data-ttu-id="0cdd9-128">`pfnCallbackThreadSet`a `pfnCallbackThreadUnset` zároveň nejsou znovu zapro.</span><span class="sxs-lookup"><span data-stu-id="0cdd9-128">`pfnCallbackThreadSet` and `pfnCallbackThreadUnset` are both non-reentrant.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0cdd9-129">Hostitelské aplikace nesmí volat `pfnCallbackThreadSet` a `pfnCallbackThreadUnset` mimo rozsah `pCallbackFunction` parametru.</span><span class="sxs-lookup"><span data-stu-id="0cdd9-129">Host applications must not call `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` outside the scope of the `pCallbackFunction` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cdd9-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0cdd9-130">Requirements</span></span>  
 <span data-ttu-id="0cdd9-131">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0cdd9-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cdd9-132">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="0cdd9-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0cdd9-133">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0cdd9-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0cdd9-134">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cdd9-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cdd9-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="0cdd9-135">See also</span></span>

- [<span data-ttu-id="0cdd9-136">ICLRMetaHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0cdd9-136">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="0cdd9-137">Hostování</span><span class="sxs-lookup"><span data-stu-id="0cdd9-137">Hosting</span></span>](index.md)
