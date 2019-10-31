---
title: ICLRTaskManager::SetLocale – metoda
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: ed16bb7f-4206-43a8-b9e9-c5737b69e3af
topic_type:
- apiref
ms.openlocfilehash: 79f24b3ccacd84037042a883d3a034bb7b4d200a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092093"
---
# <a name="iclrtaskmanagersetlocale-method"></a><span data-ttu-id="772be-102">ICLRTaskManager::SetLocale – metoda</span><span class="sxs-lookup"><span data-stu-id="772be-102">ICLRTaskManager::SetLocale Method</span></span>
<span data-ttu-id="772be-103">Upozorňuje modul CLR (Common Language Runtime) na to, že hostitel změnil hodnotu identifikátoru národního prostředí (který se mapuje na geografickou jazykovou verzi a jazyk) na aktuálně vykonávané úloze.</span><span class="sxs-lookup"><span data-stu-id="772be-103">Notifies the common language runtime (CLR) that the host has modified the value of the locale identifier (which maps to the geographical culture and language) on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="772be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="772be-104">Syntax</span></span>  
  
```cpp  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="772be-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="772be-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="772be-106">pro Hodnota identifikátoru národního prostředí, která se mapuje na nově přiřazenou geografickou jazykovou verzi a jazyk.</span><span class="sxs-lookup"><span data-stu-id="772be-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="772be-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="772be-107">Return Value</span></span>  
  
|<span data-ttu-id="772be-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="772be-108">HRESULT</span></span>|<span data-ttu-id="772be-109">Popis</span><span class="sxs-lookup"><span data-stu-id="772be-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="772be-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="772be-110">S_OK</span></span>|<span data-ttu-id="772be-111">Metoda byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="772be-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="772be-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="772be-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="772be-113">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="772be-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="772be-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="772be-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="772be-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="772be-115">The call timed out.</span></span>|  
|<span data-ttu-id="772be-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="772be-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="772be-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="772be-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="772be-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="772be-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="772be-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="772be-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="772be-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="772be-120">E_FAIL</span></span>|<span data-ttu-id="772be-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="772be-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="772be-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="772be-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="772be-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="772be-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="772be-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="772be-124">Remarks</span></span>  
 <span data-ttu-id="772be-125">`SetLocale` dává hostiteli možnost spouštět libovolné mechanismy, které by mohly být pro synchronizaci národních prostředí.</span><span class="sxs-lookup"><span data-stu-id="772be-125">`SetLocale` gives the host an opportunity to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="772be-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="772be-126">Requirements</span></span>  
 <span data-ttu-id="772be-127">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="772be-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="772be-128">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="772be-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="772be-129">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="772be-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="772be-130">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="772be-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="772be-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="772be-131">See also</span></span>

- [<span data-ttu-id="772be-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="772be-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="772be-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="772be-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="772be-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="772be-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="772be-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="772be-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
