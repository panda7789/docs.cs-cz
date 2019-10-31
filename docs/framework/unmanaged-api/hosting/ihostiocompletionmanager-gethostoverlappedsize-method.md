---
title: IHostIoCompletionManager::GetHostOverlappedSize – metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetHostOverlappedSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize
helpviewer_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize method [.NET Framework hosting]
- GetHostOverlappedSize method [.NET Framework hosting]
ms.assetid: 2902578b-d5e2-4f8d-a103-0c7b6dceda9e
topic_type:
- apiref
ms.openlocfilehash: 3c662021894acbb8eb448fa2166498254158caa4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133866"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a><span data-ttu-id="46da5-102">IHostIoCompletionManager::GetHostOverlappedSize – metoda</span><span class="sxs-lookup"><span data-stu-id="46da5-102">IHostIoCompletionManager::GetHostOverlappedSize Method</span></span>
<span data-ttu-id="46da5-103">Získá velikost libovolných vlastních dat, která hostitel chce připojit k vstupně-výstupním žádostem.</span><span class="sxs-lookup"><span data-stu-id="46da5-103">Gets the size of any custom data the host intends to append to I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46da5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46da5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46da5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="46da5-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="46da5-106">mimo Ukazatel na počet bajtů, které by měl přidělovat modul CLR (Common Language Runtime) Kromě velikosti objektu `OVERLAPPED` Win32.</span><span class="sxs-lookup"><span data-stu-id="46da5-106">[out] A pointer to the number of bytes that the common language runtime (CLR) should allocate in addition to the size of the Win32 `OVERLAPPED` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="46da5-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="46da5-107">Return Value</span></span>  
  
|<span data-ttu-id="46da5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="46da5-108">HRESULT</span></span>|<span data-ttu-id="46da5-109">Popis</span><span class="sxs-lookup"><span data-stu-id="46da5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="46da5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="46da5-110">S_OK</span></span>|<span data-ttu-id="46da5-111">`GetHostOverlappedSize` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="46da5-111">`GetHostOverlappedSize` returned successfully.</span></span>|  
|<span data-ttu-id="46da5-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="46da5-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="46da5-113">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="46da5-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="46da5-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="46da5-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="46da5-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="46da5-115">The call timed out.</span></span>|  
|<span data-ttu-id="46da5-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="46da5-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="46da5-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="46da5-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="46da5-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="46da5-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="46da5-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="46da5-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="46da5-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="46da5-120">E_FAIL</span></span>|<span data-ttu-id="46da5-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="46da5-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="46da5-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="46da5-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="46da5-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="46da5-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46da5-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="46da5-124">Remarks</span></span>  
 <span data-ttu-id="46da5-125">Všechna asynchronní vstupně-výstupní volání rozhraní API platformy Windows přebírají objekt Win32 `OVERLAPPED`, který poskytuje informace, jako je například pozice ukazatele souboru.</span><span class="sxs-lookup"><span data-stu-id="46da5-125">All asynchronous I/O calls to Windows Platform APIs take a Win32 `OVERLAPPED` object, which provides information such as the file pointer position.</span></span> <span data-ttu-id="46da5-126">Aby bylo možné zachovat stav, aplikace, které provádí asynchronní vstupně-výstupní volání, obvykle do struktury přidávají vlastní data.</span><span class="sxs-lookup"><span data-stu-id="46da5-126">To maintain state, applications that make asynchronous I/O calls typically add custom data to the structure.</span></span> <span data-ttu-id="46da5-127">`GetHostOverlappedSize` a [IHostIoCompletionManager:: InitializeHostOverlapped –](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) poskytují příležitost k tomu, aby hostitel zahrnoval taková vlastní data.</span><span class="sxs-lookup"><span data-stu-id="46da5-127">`GetHostOverlappedSize` and [IHostIoCompletionManager::InitializeHostOverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) provide an opportunity for the host to include such custom data.</span></span>  
  
 <span data-ttu-id="46da5-128">CLR volá metodu `GetHostOverlappedSize` pro určení velikosti vlastních dat, která hostitel chce připojit k objektu `OVERLAPPED`.</span><span class="sxs-lookup"><span data-stu-id="46da5-128">The CLR calls the `GetHostOverlappedSize` method to determine the size of the custom data that the host intends to append to the `OVERLAPPED` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="46da5-129">`GetHostOverlappedSize` se volá jenom jednou.</span><span class="sxs-lookup"><span data-stu-id="46da5-129">`GetHostOverlappedSize` is called only once.</span></span> <span data-ttu-id="46da5-130">Vlastní data hostitele musí mít stejnou velikost pro každou vstupně-výstupní žádost.</span><span class="sxs-lookup"><span data-stu-id="46da5-130">The host's custom data must be the same size for every I/O request.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="46da5-131">Velikost samotného objektu `OVERLAPPED` není obsažena v hodnotě `pcbSize`.</span><span class="sxs-lookup"><span data-stu-id="46da5-131">The size of the `OVERLAPPED` object itself is not included in the value of `pcbSize`.</span></span>  
  
 <span data-ttu-id="46da5-132">Další informace o struktuře `OVERLAPPED` najdete v dokumentaci k platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="46da5-132">For more information about the `OVERLAPPED` structure, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46da5-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="46da5-133">Requirements</span></span>  
 <span data-ttu-id="46da5-134">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46da5-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46da5-135">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="46da5-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="46da5-136">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="46da5-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="46da5-137">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46da5-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46da5-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="46da5-138">See also</span></span>

- <xref:System.Threading.NativeOverlapped>
- [<span data-ttu-id="46da5-139">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="46da5-139">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="46da5-140">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="46da5-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
