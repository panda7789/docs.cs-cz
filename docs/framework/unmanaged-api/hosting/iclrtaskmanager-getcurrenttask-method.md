---
title: ICLRTaskManager::GetCurrentTask – metoda
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: c0b82a9f-edc6-4878-9c81-48de53c02142
topic_type:
- apiref
ms.openlocfilehash: 9cb97d9f383b7b54b431457042c4c4a7fc9cd876
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762827"
---
# <a name="iclrtaskmanagergetcurrenttask-method"></a><span data-ttu-id="2098d-102">ICLRTaskManager::GetCurrentTask – metoda</span><span class="sxs-lookup"><span data-stu-id="2098d-102">ICLRTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="2098d-103">Získá instanci [ICLRTask](iclrtask-interface.md) , která je aktuálně spuštěna ve vlákně operačního systému, ze kterého bylo volání metody provedeno.</span><span class="sxs-lookup"><span data-stu-id="2098d-103">Gets the [ICLRTask](iclrtask-interface.md) instance that is currently running on the operating system thread from which the method call originated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2098d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2098d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTask (  
    [out] ICLRTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2098d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2098d-105">Parameters</span></span>  
 `ppTask`  
 <span data-ttu-id="2098d-106">mimo Ukazatel na adresu `ICLRTask` instance, která je aktuálně prováděna ve vlákně operačního systému, ze kterého volání vyvolala, nebo null, pokud aktuálně není v tomto vlákně prováděna žádná úloha.</span><span class="sxs-lookup"><span data-stu-id="2098d-106">[out] A pointer to the address of an `ICLRTask` instance that is currently executing on the operating system thread from which the call originated, or null if no task is currently executing on this thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2098d-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2098d-107">Return Value</span></span>  
  
|<span data-ttu-id="2098d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2098d-108">HRESULT</span></span>|<span data-ttu-id="2098d-109">Popis</span><span class="sxs-lookup"><span data-stu-id="2098d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2098d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2098d-110">S_OK</span></span>|<span data-ttu-id="2098d-111">Metoda byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="2098d-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="2098d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2098d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2098d-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="2098d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2098d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2098d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2098d-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="2098d-115">The call timed out.</span></span>|  
|<span data-ttu-id="2098d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2098d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2098d-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="2098d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2098d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2098d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2098d-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="2098d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2098d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2098d-120">E_FAIL</span></span>|<span data-ttu-id="2098d-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="2098d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2098d-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="2098d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2098d-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2098d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2098d-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2098d-124">Remarks</span></span>  
 <span data-ttu-id="2098d-125">`ICLRTask`Instance, na kterou `ppTask` parametr odkazuje, představuje aktuálně spuštěnou úlohu pro modul CLR.</span><span class="sxs-lookup"><span data-stu-id="2098d-125">The `ICLRTask` instance that the `ppTask` parameter points to represents the currently executing task for the CLR.</span></span> <span data-ttu-id="2098d-126">`ICLRTask`Instance je přidružená k odpovídající instanci [IHostTask](ihosttask-interface.md) , která představuje úlohu pro hostitele.</span><span class="sxs-lookup"><span data-stu-id="2098d-126">The `ICLRTask` instance is associated with a corresponding [IHostTask](ihosttask-interface.md) instance that represents the task for the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2098d-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2098d-127">Requirements</span></span>  
 <span data-ttu-id="2098d-128">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2098d-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2098d-129">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2098d-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2098d-130">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2098d-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2098d-131">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2098d-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2098d-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="2098d-132">See also</span></span>

- [<span data-ttu-id="2098d-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2098d-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="2098d-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2098d-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="2098d-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2098d-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="2098d-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2098d-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
