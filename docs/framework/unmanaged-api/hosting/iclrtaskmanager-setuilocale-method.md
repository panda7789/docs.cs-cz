---
title: ICLRTaskManager::SetUILocale – metoda
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.SetUILocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::SetUILocale
helpviewer_keywords:
- ICLRTaskManager::SetUILocale method [.NET Framework hosting]
- SetUILocale method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 03adaa9a-2beb-49b3-b2c4-6b4fc3f10715
topic_type:
- apiref
ms.openlocfilehash: e6ab7c7af1cf9f30f6708c4e970db619ca071343
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762770"
---
# <a name="iclrtaskmanagersetuilocale-method"></a><span data-ttu-id="7426f-102">ICLRTaskManager::SetUILocale – metoda</span><span class="sxs-lookup"><span data-stu-id="7426f-102">ICLRTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="7426f-103">Upozorňuje modul CLR (Common Language Runtime), že hostitel upravil národní prostředí (UI) uživatelského rozhraní nebo jazykovou verzi v aktuálně vykonávané úloze.</span><span class="sxs-lookup"><span data-stu-id="7426f-103">Notifies the common language runtime (CLR) that the host has modified the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7426f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7426f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7426f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7426f-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="7426f-106">pro Hodnota identifikátoru národního prostředí, která se mapuje na nově přiřazenou geografickou jazykovou verzi a jazyk pro uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7426f-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language for the user interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7426f-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7426f-107">Return Value</span></span>  
  
|<span data-ttu-id="7426f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7426f-108">HRESULT</span></span>|<span data-ttu-id="7426f-109">Popis</span><span class="sxs-lookup"><span data-stu-id="7426f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7426f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7426f-110">S_OK</span></span>|<span data-ttu-id="7426f-111">`SetUILocale`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="7426f-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="7426f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7426f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7426f-113">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="7426f-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7426f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7426f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7426f-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="7426f-115">The call timed out.</span></span>|  
|<span data-ttu-id="7426f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7426f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7426f-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="7426f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7426f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7426f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7426f-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="7426f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7426f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7426f-120">E_FAIL</span></span>|<span data-ttu-id="7426f-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="7426f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7426f-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="7426f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7426f-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7426f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7426f-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7426f-124">Remarks</span></span>  
 <span data-ttu-id="7426f-125">`SetUILocale`poskytuje příležitost pro hostitele, aby vykonává jakékoli mechanismy, které může být pro synchronizaci národních prostředí.</span><span class="sxs-lookup"><span data-stu-id="7426f-125">`SetUILocale` provides an opportunity for the host to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7426f-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7426f-126">Requirements</span></span>  
 <span data-ttu-id="7426f-127">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7426f-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7426f-128">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7426f-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7426f-129">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7426f-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7426f-130">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7426f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7426f-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="7426f-131">See also</span></span>

- [<span data-ttu-id="7426f-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7426f-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="7426f-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7426f-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="7426f-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7426f-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="7426f-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7426f-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
