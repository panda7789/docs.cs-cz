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
ms.openlocfilehash: 6713fdb822babf607752c1823a32dae43a7d567e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439594"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a><span data-ttu-id="353a4-102">IHostIoCompletionManager::GetHostOverlappedSize – metoda</span><span class="sxs-lookup"><span data-stu-id="353a4-102">IHostIoCompletionManager::GetHostOverlappedSize Method</span></span>
<span data-ttu-id="353a4-103">Získá velikost vlastní data, která hostitele chtít připojit k vstupně-výstupní požadavky.</span><span class="sxs-lookup"><span data-stu-id="353a4-103">Gets the size of any custom data the host intends to append to I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="353a4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="353a4-104">Syntax</span></span>  
  
```  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="353a4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="353a4-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="353a4-106">[out] Ukazatel na počet bajtů, které modul CLR (CLR) přidělovat kromě velikost Win32 `OVERLAPPED` objektu.</span><span class="sxs-lookup"><span data-stu-id="353a4-106">[out] A pointer to the number of bytes that the common language runtime (CLR) should allocate in addition to the size of the Win32 `OVERLAPPED` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="353a4-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="353a4-107">Return Value</span></span>  
  
|<span data-ttu-id="353a4-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="353a4-108">HRESULT</span></span>|<span data-ttu-id="353a4-109">Popis</span><span class="sxs-lookup"><span data-stu-id="353a4-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="353a4-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="353a4-110">S_OK</span></span>|<span data-ttu-id="353a4-111">`GetHostOverlappedSize` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="353a4-111">`GetHostOverlappedSize` returned successfully.</span></span>|  
|<span data-ttu-id="353a4-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="353a4-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="353a4-113">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="353a4-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="353a4-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="353a4-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="353a4-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="353a4-115">The call timed out.</span></span>|  
|<span data-ttu-id="353a4-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="353a4-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="353a4-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="353a4-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="353a4-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="353a4-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="353a4-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="353a4-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="353a4-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="353a4-120">E_FAIL</span></span>|<span data-ttu-id="353a4-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="353a4-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="353a4-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="353a4-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="353a4-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="353a4-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="353a4-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="353a4-124">Remarks</span></span>  
 <span data-ttu-id="353a4-125">Všechna volání asynchronní vstupně-výstupních operací do rozhraní API platformy systému Windows trvat Win32 `OVERLAPPED` objekt, který poskytuje informace, jako je ukazatel pozice v souboru.</span><span class="sxs-lookup"><span data-stu-id="353a4-125">All asynchronous I/O calls to Windows Platform APIs take a Win32 `OVERLAPPED` object, which provides information such as the file pointer position.</span></span> <span data-ttu-id="353a4-126">Aplikace, které obvykle provádět volání asynchronní vstupně-výstupních operací pro uchování stavu, přidejte vlastní data na strukturu.</span><span class="sxs-lookup"><span data-stu-id="353a4-126">To maintain state, applications that make asynchronous I/O calls typically add custom data to the structure.</span></span> <span data-ttu-id="353a4-127">`GetHostOverlappedSize` a [ihostiocompletionmanager::initializehostoverlapped –](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) nabízejí možnost pro hostitele zahrnout taková vlastní data.</span><span class="sxs-lookup"><span data-stu-id="353a4-127">`GetHostOverlappedSize` and [IHostIoCompletionManager::InitializeHostOverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) provide an opportunity for the host to include such custom data.</span></span>  
  
 <span data-ttu-id="353a4-128">Volání CLR `GetHostOverlappedSize` metoda k určení velikosti vlastních dat, kterou chce připojit k hostiteli `OVERLAPPED` objektu.</span><span class="sxs-lookup"><span data-stu-id="353a4-128">The CLR calls the `GetHostOverlappedSize` method to determine the size of the custom data that the host intends to append to the `OVERLAPPED` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="353a4-129">`GetHostOverlappedSize` je volat pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="353a4-129">`GetHostOverlappedSize` is called only once.</span></span> <span data-ttu-id="353a4-130">Vlastní data hostitele musí mít stejnou velikost pro každý požadavek vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="353a4-130">The host's custom data must be the same size for every I/O request.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="353a4-131">Velikost `OVERLAPPED` samotného objektu není zahrnutý v hodnotě `pcbSize`.</span><span class="sxs-lookup"><span data-stu-id="353a4-131">The size of the `OVERLAPPED` object itself is not included in the value of `pcbSize`.</span></span>  
  
 <span data-ttu-id="353a4-132">Další informace o `OVERLAPPED` struktury najdete v dokumentaci k platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="353a4-132">For more information about the `OVERLAPPED` structure, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="353a4-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="353a4-133">Requirements</span></span>  
 <span data-ttu-id="353a4-134">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="353a4-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="353a4-135">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="353a4-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="353a4-136">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="353a4-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="353a4-137">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="353a4-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="353a4-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="353a4-138">See Also</span></span>  
 <xref:System.Threading.NativeOverlapped>  
 [<span data-ttu-id="353a4-139">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="353a4-139">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="353a4-140">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="353a4-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
