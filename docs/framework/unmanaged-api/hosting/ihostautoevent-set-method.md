---
title: IHostAutoEvent::Set – metoda
ms.date: 03/30/2017
api_name:
- IHostAutoEvent.Set
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent::Set
helpviewer_keywords:
- Set method, IHostAutoEvent interface [.NET Framework hosting]
- IHostAutoEvent::Set method [.NET Framework hosting]
ms.assetid: 46becf3e-bc0e-4338-85c0-9ab0df76a1d0
topic_type:
- apiref
ms.openlocfilehash: 55fd858927743b097e5e842c0897a16d36b76733
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804987"
---
# <a name="ihostautoeventset-method"></a><span data-ttu-id="2f5a3-102">IHostAutoEvent::Set – metoda</span><span class="sxs-lookup"><span data-stu-id="2f5a3-102">IHostAutoEvent::Set Method</span></span>
<span data-ttu-id="2f5a3-103">Nastaví aktuální instanci [IHostAutoEvent](ihostautoevent-interface.md) na signálový stav.</span><span class="sxs-lookup"><span data-stu-id="2f5a3-103">Sets the current [IHostAutoEvent](ihostautoevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f5a3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f5a3-104">Syntax</span></span>  
  
```cpp  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2f5a3-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2f5a3-105">Return Value</span></span>  
  
|<span data-ttu-id="2f5a3-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2f5a3-106">HRESULT</span></span>|<span data-ttu-id="2f5a3-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2f5a3-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2f5a3-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="2f5a3-108">S_OK</span></span>|<span data-ttu-id="2f5a3-109">`Set`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="2f5a3-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="2f5a3-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2f5a3-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2f5a3-111">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="2f5a3-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2f5a3-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2f5a3-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2f5a3-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="2f5a3-113">The call timed out.</span></span>|  
|<span data-ttu-id="2f5a3-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2f5a3-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2f5a3-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="2f5a3-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2f5a3-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2f5a3-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2f5a3-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="2f5a3-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2f5a3-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2f5a3-118">E_FAIL</span></span>|<span data-ttu-id="2f5a3-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="2f5a3-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2f5a3-120">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="2f5a3-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2f5a3-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2f5a3-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2f5a3-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2f5a3-122">Requirements</span></span>  
 <span data-ttu-id="2f5a3-123">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f5a3-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f5a3-124">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2f5a3-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2f5a3-125">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2f5a3-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2f5a3-126">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f5a3-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f5a3-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="2f5a3-127">See also</span></span>

- [<span data-ttu-id="2f5a3-128">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f5a3-128">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="2f5a3-129">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f5a3-129">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="2f5a3-130">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f5a3-130">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="2f5a3-131">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f5a3-131">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
