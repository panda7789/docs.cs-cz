---
title: IHostTaskManager::SetLocale – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: 747ee407-ee8c-484d-9583-25089236d2d1
topic_type:
- apiref
ms.openlocfilehash: 841827017262b731fd5e6f6bd0b5862fecaf2744
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841721"
---
# <a name="ihosttaskmanagersetlocale-method"></a><span data-ttu-id="f12b7-102">IHostTaskManager::SetLocale – metoda</span><span class="sxs-lookup"><span data-stu-id="f12b7-102">IHostTaskManager::SetLocale Method</span></span>
<span data-ttu-id="f12b7-103">Upozorňuje hostitele, že modul CLR (Common Language Runtime) změnil národní prostředí nebo jazykovou verzi v aktuálně vykonávané úloze.</span><span class="sxs-lookup"><span data-stu-id="f12b7-103">Notifies the host that the common language runtime (CLR) has changed the locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f12b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f12b7-104">Syntax</span></span>  
  
```cpp  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f12b7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f12b7-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="f12b7-106">pro Hodnota identifikátoru národního prostředí, která se mapuje na nově přiřazenou geografickou jazykovou verzi a jazyk.</span><span class="sxs-lookup"><span data-stu-id="f12b7-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f12b7-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f12b7-107">Return Value</span></span>  
  
|<span data-ttu-id="f12b7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f12b7-108">HRESULT</span></span>|<span data-ttu-id="f12b7-109">Popis</span><span class="sxs-lookup"><span data-stu-id="f12b7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f12b7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f12b7-110">S_OK</span></span>|<span data-ttu-id="f12b7-111">`SetLocale`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="f12b7-111">`SetLocale` returned successfully.</span></span>|  
|<span data-ttu-id="f12b7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f12b7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f12b7-113">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="f12b7-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f12b7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f12b7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f12b7-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="f12b7-115">The call timed out.</span></span>|  
|<span data-ttu-id="f12b7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f12b7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f12b7-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="f12b7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f12b7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f12b7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f12b7-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="f12b7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f12b7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f12b7-120">E_FAIL</span></span>|<span data-ttu-id="f12b7-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="f12b7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f12b7-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="f12b7-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f12b7-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f12b7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f12b7-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="f12b7-124">E_NOTIMPL</span></span>|<span data-ttu-id="f12b7-125">Hostitel nepovoluje spravovanému kódu uživatele upravovat národní prostředí.</span><span class="sxs-lookup"><span data-stu-id="f12b7-125">The host does not allow managed user code to modify the locale.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f12b7-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f12b7-126">Remarks</span></span>  
 <span data-ttu-id="f12b7-127">Běhové prostředí volá `SetLocale` při <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> změně hodnoty vlastnosti spravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="f12b7-127">The runtime calls `SetLocale` when the value of the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="f12b7-128">Tato metoda poskytuje možnost pro hostitele, aby vykonává jakékoli mechanismy, které může být pro synchronizaci národních prostředí.</span><span class="sxs-lookup"><span data-stu-id="f12b7-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="f12b7-129">Pokud hostitel nepovoluje změnu národního prostředí ze spravovaného kódu nebo neimplementuje mechanismus pro synchronizaci místních hodnot, měla by vrátit E_NOTIMPL z této metody.</span><span class="sxs-lookup"><span data-stu-id="f12b7-129">If a host does not allow the locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f12b7-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f12b7-130">Requirements</span></span>  
 <span data-ttu-id="f12b7-131">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f12b7-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f12b7-132">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f12b7-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f12b7-133">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f12b7-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f12b7-134">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f12b7-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f12b7-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="f12b7-135">See also</span></span>

- [<span data-ttu-id="f12b7-136">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f12b7-136">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="f12b7-137">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f12b7-137">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="f12b7-138">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f12b7-138">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="f12b7-139">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f12b7-139">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="f12b7-140">SetUILocale – metoda</span><span class="sxs-lookup"><span data-stu-id="f12b7-140">SetUILocale Method</span></span>](ihosttaskmanager-setuilocale-method.md)
