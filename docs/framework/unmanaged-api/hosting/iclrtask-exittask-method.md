---
title: ICLRTask::ExitTask – metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.ExitTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::ExitTask
helpviewer_keywords:
- ExitTask method [.NET Framework hosting]
- ICLRTask::ExitTask method [.NET Framework hosting]
ms.assetid: 746c85a6-4b33-4f72-a2e9-379fdf2e96af
topic_type:
- apiref
ms.openlocfilehash: 9294f149e020cfb22512b4f110d64c5dabb5e777
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762445"
---
# <a name="iclrtaskexittask-method"></a><span data-ttu-id="2f8c1-102">ICLRTask::ExitTask – metoda</span><span class="sxs-lookup"><span data-stu-id="2f8c1-102">ICLRTask::ExitTask Method</span></span>
<span data-ttu-id="2f8c1-103">Upozorní modul CLR (Common Language Runtime) na ukončení úlohy reprezentované aktuální instancí [ICLRTask](iclrtask-interface.md) a pokusí se o řádné ukončení úlohy.</span><span class="sxs-lookup"><span data-stu-id="2f8c1-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](iclrtask-interface.md) instance is ending, and attempts to shut the task down gracefully.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f8c1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f8c1-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2f8c1-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2f8c1-105">Return Value</span></span>  
  
|<span data-ttu-id="2f8c1-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2f8c1-106">HRESULT</span></span>|<span data-ttu-id="2f8c1-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2f8c1-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2f8c1-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="2f8c1-108">S_OK</span></span>|<span data-ttu-id="2f8c1-109">`ExitTask`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="2f8c1-109">`ExitTask` returned successfully.</span></span>|  
|<span data-ttu-id="2f8c1-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2f8c1-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2f8c1-111">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="2f8c1-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2f8c1-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2f8c1-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2f8c1-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="2f8c1-113">The call timed out.</span></span>|  
|<span data-ttu-id="2f8c1-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2f8c1-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2f8c1-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="2f8c1-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2f8c1-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2f8c1-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2f8c1-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="2f8c1-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2f8c1-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2f8c1-118">E_FAIL</span></span>|<span data-ttu-id="2f8c1-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="2f8c1-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2f8c1-120">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="2f8c1-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2f8c1-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2f8c1-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f8c1-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2f8c1-122">Remarks</span></span>  
 <span data-ttu-id="2f8c1-123">`ExitTask`pokusí se vyčistit úlohu čistým vypnutím způsobem, který je podobný odpojování vlákna z nespravované knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="2f8c1-123">`ExitTask` attempts a clean shutdown of a task, in a manner analogous to detaching a thread from an unmanaged type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f8c1-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2f8c1-124">Requirements</span></span>  
 <span data-ttu-id="2f8c1-125">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f8c1-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f8c1-126">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2f8c1-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2f8c1-127">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2f8c1-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2f8c1-128">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f8c1-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f8c1-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="2f8c1-129">See also</span></span>

- [<span data-ttu-id="2f8c1-130">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f8c1-130">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="2f8c1-131">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f8c1-131">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="2f8c1-132">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f8c1-132">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="2f8c1-133">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f8c1-133">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
