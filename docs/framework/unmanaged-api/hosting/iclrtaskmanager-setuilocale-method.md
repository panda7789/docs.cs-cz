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
ms.openlocfilehash: 051bd5cb846eb4e6e3390e17b3011a1c5b50bc45
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127865"
---
# <a name="iclrtaskmanagersetuilocale-method"></a><span data-ttu-id="314ff-102">ICLRTaskManager::SetUILocale – metoda</span><span class="sxs-lookup"><span data-stu-id="314ff-102">ICLRTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="314ff-103">Upozorňuje modul CLR (Common Language Runtime), že hostitel upravil národní prostředí (UI) uživatelského rozhraní nebo jazykovou verzi v aktuálně vykonávané úloze.</span><span class="sxs-lookup"><span data-stu-id="314ff-103">Notifies the common language runtime (CLR) that the host has modified the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="314ff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="314ff-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="314ff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="314ff-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="314ff-106">pro Hodnota identifikátoru národního prostředí, která se mapuje na nově přiřazenou geografickou jazykovou verzi a jazyk pro uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="314ff-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language for the user interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="314ff-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="314ff-107">Return Value</span></span>  
  
|<span data-ttu-id="314ff-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="314ff-108">HRESULT</span></span>|<span data-ttu-id="314ff-109">Popis</span><span class="sxs-lookup"><span data-stu-id="314ff-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="314ff-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="314ff-110">S_OK</span></span>|<span data-ttu-id="314ff-111">`SetUILocale` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="314ff-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="314ff-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="314ff-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="314ff-113">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="314ff-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="314ff-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="314ff-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="314ff-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="314ff-115">The call timed out.</span></span>|  
|<span data-ttu-id="314ff-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="314ff-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="314ff-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="314ff-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="314ff-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="314ff-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="314ff-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="314ff-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="314ff-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="314ff-120">E_FAIL</span></span>|<span data-ttu-id="314ff-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="314ff-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="314ff-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="314ff-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="314ff-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="314ff-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="314ff-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="314ff-124">Remarks</span></span>  
 <span data-ttu-id="314ff-125">`SetUILocale` poskytuje možnost, aby hostitel spouštěl všechny mechanismy, které by mohly být pro synchronizaci národních prostředí.</span><span class="sxs-lookup"><span data-stu-id="314ff-125">`SetUILocale` provides an opportunity for the host to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="314ff-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="314ff-126">Requirements</span></span>  
 <span data-ttu-id="314ff-127">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="314ff-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="314ff-128">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="314ff-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="314ff-129">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="314ff-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="314ff-130">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="314ff-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="314ff-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="314ff-131">See also</span></span>

- [<span data-ttu-id="314ff-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="314ff-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="314ff-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="314ff-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="314ff-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="314ff-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="314ff-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="314ff-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
