---
title: IHostTaskManager::SetUILocale – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetUILocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetUILocale
helpviewer_keywords:
- SetUILocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetUILocale method [.NET Framework hosting]
ms.assetid: d0c87a9c-ea81-4237-a16b-c22b36ec9dc8
topic_type:
- apiref
ms.openlocfilehash: e7e65c3b9bcafdf4c8b1185fcff1fc0740b2ef7c
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841426"
---
# <a name="ihosttaskmanagersetuilocale-method"></a><span data-ttu-id="c3b48-102">IHostTaskManager::SetUILocale – metoda</span><span class="sxs-lookup"><span data-stu-id="c3b48-102">IHostTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="c3b48-103">Upozorňuje hostitele, že modul CLR (Common Language Runtime) změnil národní prostředí nebo jazykovou verzi v aktuálně vykonávané úloze.</span><span class="sxs-lookup"><span data-stu-id="c3b48-103">Notifies the host that the common language runtime (CLR) has changed the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3b48-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3b48-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3b48-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c3b48-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="c3b48-106">pro Hodnota identifikátoru národního prostředí, která se mapuje na nově přiřazenou geografickou jazykovou verzi a jazyk.</span><span class="sxs-lookup"><span data-stu-id="c3b48-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3b48-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c3b48-107">Return Value</span></span>  
  
|<span data-ttu-id="c3b48-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c3b48-108">HRESULT</span></span>|<span data-ttu-id="c3b48-109">Popis</span><span class="sxs-lookup"><span data-stu-id="c3b48-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c3b48-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c3b48-110">S_OK</span></span>|<span data-ttu-id="c3b48-111">`SetUILocale`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="c3b48-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="c3b48-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c3b48-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c3b48-113">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c3b48-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c3b48-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c3b48-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c3b48-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="c3b48-115">The call timed out.</span></span>|  
|<span data-ttu-id="c3b48-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c3b48-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c3b48-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="c3b48-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c3b48-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c3b48-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c3b48-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="c3b48-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c3b48-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c3b48-120">E_FAIL</span></span>|<span data-ttu-id="c3b48-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="c3b48-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c3b48-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="c3b48-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c3b48-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c3b48-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c3b48-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="c3b48-124">E_NOTIMPL</span></span>|<span data-ttu-id="c3b48-125">Hostitel neumožňuje spravovanému uživatelskému kódu změnit jazykovou verzi uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c3b48-125">The host does not allow managed user code to change the UI culture.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3b48-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c3b48-126">Remarks</span></span>  
 <span data-ttu-id="c3b48-127">Běhové prostředí volá `SetUILocale` při <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> změně hodnoty vlastnosti spravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="c3b48-127">The runtime calls `SetUILocale` when the value of the <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="c3b48-128">Tato metoda poskytuje možnost pro hostitele, aby vykonává jakékoli mechanismy, které může být pro synchronizaci národních prostředí.</span><span class="sxs-lookup"><span data-stu-id="c3b48-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="c3b48-129">Pokud hostitel nepovoluje změnu národního prostředí uživatelského rozhraní ze spravovaného kódu nebo neimplementuje mechanismus pro synchronizaci místních hodnot, měla by vrátit E_NOTIMPL z této metody.</span><span class="sxs-lookup"><span data-stu-id="c3b48-129">If a host does not allow the UI locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3b48-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c3b48-130">Requirements</span></span>  
 <span data-ttu-id="c3b48-131">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3b48-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3b48-132">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c3b48-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c3b48-133">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c3b48-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c3b48-134">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3b48-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3b48-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="c3b48-135">See also</span></span>

- [<span data-ttu-id="c3b48-136">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c3b48-136">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="c3b48-137">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c3b48-137">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="c3b48-138">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c3b48-138">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="c3b48-139">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c3b48-139">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="c3b48-140">SetLocale – metoda</span><span class="sxs-lookup"><span data-stu-id="c3b48-140">SetLocale Method</span></span>](ihosttaskmanager-setlocale-method.md)
