---
title: ICLRSyncManager::GetMonitorOwner – metoda
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.GetMonitorOwner
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::GetMonitorOwner
helpviewer_keywords:
- ICLRSyncManager::GetMonitorOwner method [.NET Framework hosting]
- GetMonitorOwner method [.NET Framework hosting]
ms.assetid: 840983a4-396d-47b4-86a0-d35f9b437cdb
topic_type:
- apiref
ms.openlocfilehash: 77debe047f5b379237022f44ef8f9d96718b227d
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762497"
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a><span data-ttu-id="a2e9c-102">ICLRSyncManager::GetMonitorOwner – metoda</span><span class="sxs-lookup"><span data-stu-id="a2e9c-102">ICLRSyncManager::GetMonitorOwner Method</span></span>
<span data-ttu-id="a2e9c-103">Získá instanci [IHostTask](ihosttask-interface.md) , která vlastní monitor identifikovaný zadaným souborem cookie.</span><span class="sxs-lookup"><span data-stu-id="a2e9c-103">Gets the [IHostTask](ihosttask-interface.md) instance that owns the monitor identified by the specified cookie.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2e9c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2e9c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2e9c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a2e9c-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="a2e9c-106">pro Soubor cookie přidružený k monitoru</span><span class="sxs-lookup"><span data-stu-id="a2e9c-106">[in] The cookie associated with the monitor.</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="a2e9c-107">mimo Ukazatel na `IHostTask` , který aktuálně vlastní monitor, nebo hodnotu null, pokud nemá žádná úloha vlastnictví.</span><span class="sxs-lookup"><span data-stu-id="a2e9c-107">[out] A pointer to the `IHostTask` that currently owns the monitor, or null if no task has ownership.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2e9c-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a2e9c-108">Return Value</span></span>  
  
|<span data-ttu-id="a2e9c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a2e9c-109">HRESULT</span></span>|<span data-ttu-id="a2e9c-110">Popis</span><span class="sxs-lookup"><span data-stu-id="a2e9c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a2e9c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a2e9c-111">S_OK</span></span>|<span data-ttu-id="a2e9c-112">`GetMonitorOwner`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="a2e9c-112">`GetMonitorOwner` returned successfully.</span></span>|  
|<span data-ttu-id="a2e9c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a2e9c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a2e9c-114">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="a2e9c-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a2e9c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a2e9c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a2e9c-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="a2e9c-116">The call timed out.</span></span>|  
|<span data-ttu-id="a2e9c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a2e9c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a2e9c-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="a2e9c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a2e9c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a2e9c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a2e9c-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="a2e9c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a2e9c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a2e9c-121">E_FAIL</span></span>|<span data-ttu-id="a2e9c-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="a2e9c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a2e9c-123">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="a2e9c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a2e9c-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a2e9c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2e9c-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a2e9c-125">Remarks</span></span>  
 <span data-ttu-id="a2e9c-126">Hostitel obvykle volá `GetMonitorOwner` jako součást mechanismu zjišťování vzájemného zablokování.</span><span class="sxs-lookup"><span data-stu-id="a2e9c-126">The host typically calls `GetMonitorOwner` as part of a deadlock-detection mechanism.</span></span> <span data-ttu-id="a2e9c-127">Soubor cookie je přidružen k monitoru, když je vytvořen pomocí volání metody [IHostSyncManager:: CreateMonitorEvent –](ihostsyncmanager-createmonitorevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="a2e9c-127">The cookie is associated with a monitor when it is created by using a call to [IHostSyncManager::CreateMonitorEvent](ihostsyncmanager-createmonitorevent-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a2e9c-128">Volání pro vydanou událost, která je podkladem, může monitor blokovat – ale nebude zablokovat – Pokud je volání této metody aktuálně platné pro soubor cookie přidružený k tomuto monitoru.</span><span class="sxs-lookup"><span data-stu-id="a2e9c-128">A call to release the event underlying the monitor might block—but will not deadlock—if a call to this method is currently in effect on the cookie associated with that monitor.</span></span> <span data-ttu-id="a2e9c-129">Jiné úlohy mohou také zablokovat, pokud se pokusí získat toto monitorování.</span><span class="sxs-lookup"><span data-stu-id="a2e9c-129">Other tasks might also block if they attempt to acquire this monitor.</span></span>  
  
 <span data-ttu-id="a2e9c-130">`GetMonitorOwner`vždy vrátí hodnotu okamžitě a lze ji volat kdykoli po volání `CreateMonitorEvent` .</span><span class="sxs-lookup"><span data-stu-id="a2e9c-130">`GetMonitorOwner` always returns immediately and can be called any time after a call to `CreateMonitorEvent`.</span></span> <span data-ttu-id="a2e9c-131">Hostitel nemusí čekat, dokud úloha nečeká na událost.</span><span class="sxs-lookup"><span data-stu-id="a2e9c-131">The host does not need to wait until a task is waiting on the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2e9c-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a2e9c-132">Requirements</span></span>  
 <span data-ttu-id="a2e9c-133">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2e9c-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2e9c-134">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a2e9c-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a2e9c-135">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a2e9c-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a2e9c-136">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2e9c-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2e9c-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="a2e9c-137">See also</span></span>

- [<span data-ttu-id="a2e9c-138">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a2e9c-138">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="a2e9c-139">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a2e9c-139">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
