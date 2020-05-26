---
title: IHostIoCompletionManager::SetCLRIoCompletionManager – metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetCLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager method [.NET Framework hosting]
- SetCLRIoCompletionManager method [.NET Framework hosting]
ms.assetid: 4254bb01-3a14-4f34-a3be-60ff1f5072b5
topic_type:
- apiref
ms.openlocfilehash: a76e807e6b316fc4b904e3f085a17b00d6a11c73
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804701"
---
# <a name="ihostiocompletionmanagersetclriocompletionmanager-method"></a><span data-ttu-id="6e662-102">IHostIoCompletionManager::SetCLRIoCompletionManager – metoda</span><span class="sxs-lookup"><span data-stu-id="6e662-102">IHostIoCompletionManager::SetCLRIoCompletionManager Method</span></span>
<span data-ttu-id="6e662-103">Poskytuje hostitele s ukazatelem rozhraní instance [ICLRIoCompletionManager –](iclriocompletionmanager-interface.md) implementované modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="6e662-103">Provides the host with an interface pointer to the [ICLRIoCompletionManager](iclriocompletionmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e662-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e662-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRIoCompletionManager (  
    [in] ICLRIoCompletionManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e662-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6e662-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="6e662-106">pro Ukazatel rozhraní na `ICLRIoCompletionManager` instanci poskytnutou modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="6e662-106">[in] An interface pointer to an `ICLRIoCompletionManager` instance provided by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6e662-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6e662-107">Return Value</span></span>  
  
|<span data-ttu-id="6e662-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6e662-108">HRESULT</span></span>|<span data-ttu-id="6e662-109">Popis</span><span class="sxs-lookup"><span data-stu-id="6e662-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6e662-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6e662-110">S_OK</span></span>|<span data-ttu-id="6e662-111">`SetCLRIoCompletionManager`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="6e662-111">`SetCLRIoCompletionManager` returned successfully.</span></span>|  
|<span data-ttu-id="6e662-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6e662-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6e662-113">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="6e662-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6e662-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6e662-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6e662-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="6e662-115">The call timed out.</span></span>|  
|<span data-ttu-id="6e662-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6e662-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6e662-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="6e662-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6e662-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6e662-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6e662-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="6e662-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6e662-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6e662-120">E_FAIL</span></span>|<span data-ttu-id="6e662-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="6e662-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6e662-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="6e662-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6e662-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6e662-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e662-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6e662-124">Remarks</span></span>  
 <span data-ttu-id="6e662-125">Po volání CLR `SetCLRIoCompletionManager` musí hostitel volat [ICLRIoCompletionManager –::](iclriocompletionmanager-oncomplete-method.md) Completed pro oznamování CLR, když požadavek na vstup/výstup byl dokončen.</span><span class="sxs-lookup"><span data-stu-id="6e662-125">After the CLR has called `SetCLRIoCompletionManager`, the host must call [ICLRIoCompletionManager::OnComplete](iclriocompletionmanager-oncomplete-method.md) to notify the CLR when an I/O request has been completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e662-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6e662-126">Requirements</span></span>  
 <span data-ttu-id="6e662-127">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e662-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e662-128">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6e662-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6e662-129">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6e662-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6e662-130">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e662-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e662-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e662-131">See also</span></span>

- [<span data-ttu-id="6e662-132">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6e662-132">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="6e662-133">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6e662-133">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
