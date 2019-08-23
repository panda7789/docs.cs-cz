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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c43f906961b9e76d5f0f34ba5a5b2f656f5b1488
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937506"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a><span data-ttu-id="b656c-102">IHostIoCompletionManager::GetHostOverlappedSize – metoda</span><span class="sxs-lookup"><span data-stu-id="b656c-102">IHostIoCompletionManager::GetHostOverlappedSize Method</span></span>
<span data-ttu-id="b656c-103">Získá velikost libovolných vlastních dat, která hostitel chce připojit k vstupně-výstupním žádostem.</span><span class="sxs-lookup"><span data-stu-id="b656c-103">Gets the size of any custom data the host intends to append to I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b656c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b656c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b656c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b656c-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="b656c-106">mimo Ukazatel na počet bajtů, které by měl přidělovat modul CLR (Common Language Runtime) Kromě velikosti objektu Win32 `OVERLAPPED` .</span><span class="sxs-lookup"><span data-stu-id="b656c-106">[out] A pointer to the number of bytes that the common language runtime (CLR) should allocate in addition to the size of the Win32 `OVERLAPPED` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b656c-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b656c-107">Return Value</span></span>  
  
|<span data-ttu-id="b656c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b656c-108">HRESULT</span></span>|<span data-ttu-id="b656c-109">Popis</span><span class="sxs-lookup"><span data-stu-id="b656c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b656c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b656c-110">S_OK</span></span>|<span data-ttu-id="b656c-111">`GetHostOverlappedSize`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="b656c-111">`GetHostOverlappedSize` returned successfully.</span></span>|  
|<span data-ttu-id="b656c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b656c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b656c-113">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="b656c-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b656c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b656c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b656c-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="b656c-115">The call timed out.</span></span>|  
|<span data-ttu-id="b656c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b656c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b656c-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="b656c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b656c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b656c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b656c-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="b656c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b656c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b656c-120">E_FAIL</span></span>|<span data-ttu-id="b656c-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="b656c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b656c-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="b656c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b656c-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b656c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b656c-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b656c-124">Remarks</span></span>  
 <span data-ttu-id="b656c-125">Všechna asynchronní vstupně-výstupní volání rozhraní API platformy Windows přebírají objekt `OVERLAPPED` Win32, který poskytuje informace, jako je například pozice ukazatele souboru.</span><span class="sxs-lookup"><span data-stu-id="b656c-125">All asynchronous I/O calls to Windows Platform APIs take a Win32 `OVERLAPPED` object, which provides information such as the file pointer position.</span></span> <span data-ttu-id="b656c-126">Aby bylo možné zachovat stav, aplikace, které provádí asynchronní vstupně-výstupní volání, obvykle do struktury přidávají vlastní data.</span><span class="sxs-lookup"><span data-stu-id="b656c-126">To maintain state, applications that make asynchronous I/O calls typically add custom data to the structure.</span></span> <span data-ttu-id="b656c-127">`GetHostOverlappedSize`a [IHostIoCompletionManager:: InitializeHostOverlapped –](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) poskytují příležitost k tomu, aby hostitel zahrnoval taková vlastní data.</span><span class="sxs-lookup"><span data-stu-id="b656c-127">`GetHostOverlappedSize` and [IHostIoCompletionManager::InitializeHostOverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) provide an opportunity for the host to include such custom data.</span></span>  
  
 <span data-ttu-id="b656c-128">CLR volá `GetHostOverlappedSize` metodu pro určení velikosti vlastních dat, která hostitel chce připojit `OVERLAPPED` k objektu.</span><span class="sxs-lookup"><span data-stu-id="b656c-128">The CLR calls the `GetHostOverlappedSize` method to determine the size of the custom data that the host intends to append to the `OVERLAPPED` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b656c-129">`GetHostOverlappedSize`se volá jenom jednou.</span><span class="sxs-lookup"><span data-stu-id="b656c-129">`GetHostOverlappedSize` is called only once.</span></span> <span data-ttu-id="b656c-130">Vlastní data hostitele musí mít stejnou velikost pro každou vstupně-výstupní žádost.</span><span class="sxs-lookup"><span data-stu-id="b656c-130">The host's custom data must be the same size for every I/O request.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b656c-131">Velikost `OVERLAPPED` samotného objektu není obsažena v `pcbSize`hodnotě.</span><span class="sxs-lookup"><span data-stu-id="b656c-131">The size of the `OVERLAPPED` object itself is not included in the value of `pcbSize`.</span></span>  
  
 <span data-ttu-id="b656c-132">Další informace o `OVERLAPPED` struktuře najdete v dokumentaci k platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="b656c-132">For more information about the `OVERLAPPED` structure, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b656c-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b656c-133">Requirements</span></span>  
 <span data-ttu-id="b656c-134">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b656c-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b656c-135">**Hlaviček** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b656c-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b656c-136">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b656c-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b656c-137">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b656c-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b656c-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b656c-138">See also</span></span>

- <xref:System.Threading.NativeOverlapped>
- [<span data-ttu-id="b656c-139">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b656c-139">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="b656c-140">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b656c-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
