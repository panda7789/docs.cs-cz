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
ms.openlocfilehash: 54e72205f8f976498df3b1fe1e055fb7df12d68e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780685"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a><span data-ttu-id="bccd6-102">IHostIoCompletionManager::GetHostOverlappedSize – metoda</span><span class="sxs-lookup"><span data-stu-id="bccd6-102">IHostIoCompletionManager::GetHostOverlappedSize Method</span></span>
<span data-ttu-id="bccd6-103">Získá velikost vlastní data, která si klade za cíl hostitele pro připojení k vstupně-výstupní požadavky.</span><span class="sxs-lookup"><span data-stu-id="bccd6-103">Gets the size of any custom data the host intends to append to I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bccd6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bccd6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bccd6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bccd6-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="bccd6-106">[out] Ukazatel na počet bajtů, které modul CLR (CLR) přidělovat kromě velikost Win32 `OVERLAPPED` objektu.</span><span class="sxs-lookup"><span data-stu-id="bccd6-106">[out] A pointer to the number of bytes that the common language runtime (CLR) should allocate in addition to the size of the Win32 `OVERLAPPED` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bccd6-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bccd6-107">Return Value</span></span>  
  
|<span data-ttu-id="bccd6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bccd6-108">HRESULT</span></span>|<span data-ttu-id="bccd6-109">Popis</span><span class="sxs-lookup"><span data-stu-id="bccd6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bccd6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bccd6-110">S_OK</span></span>|<span data-ttu-id="bccd6-111">`GetHostOverlappedSize` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="bccd6-111">`GetHostOverlappedSize` returned successfully.</span></span>|  
|<span data-ttu-id="bccd6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bccd6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bccd6-113">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="bccd6-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bccd6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bccd6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bccd6-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="bccd6-115">The call timed out.</span></span>|  
|<span data-ttu-id="bccd6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bccd6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bccd6-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="bccd6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bccd6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bccd6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bccd6-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="bccd6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bccd6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bccd6-120">E_FAIL</span></span>|<span data-ttu-id="bccd6-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="bccd6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bccd6-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="bccd6-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bccd6-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bccd6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bccd6-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bccd6-124">Remarks</span></span>  
 <span data-ttu-id="bccd6-125">Všechna volání asynchronní vstupně-výstupních operací do rozhraní API platformy Windows trvat Win32 `OVERLAPPED` objektu, který poskytuje informace, jako je ukazatel pozice v souboru.</span><span class="sxs-lookup"><span data-stu-id="bccd6-125">All asynchronous I/O calls to Windows Platform APIs take a Win32 `OVERLAPPED` object, which provides information such as the file pointer position.</span></span> <span data-ttu-id="bccd6-126">Pro uchování stavu aplikace, které obvykle provádět volání asynchronní vstupně-výstupních operací přidání vlastních dat do struktury.</span><span class="sxs-lookup"><span data-stu-id="bccd6-126">To maintain state, applications that make asynchronous I/O calls typically add custom data to the structure.</span></span> <span data-ttu-id="bccd6-127">`GetHostOverlappedSize` a [ihostiocompletionmanager::initializehostoverlapped –](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) poskytnout příležitosti pro hostitele zahrnout tyto vlastní data.</span><span class="sxs-lookup"><span data-stu-id="bccd6-127">`GetHostOverlappedSize` and [IHostIoCompletionManager::InitializeHostOverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) provide an opportunity for the host to include such custom data.</span></span>  
  
 <span data-ttu-id="bccd6-128">Volání CLR `GetHostOverlappedSize` metodu pro určení velikosti vlastní data, která chce připojit k hostiteli `OVERLAPPED` objektu.</span><span class="sxs-lookup"><span data-stu-id="bccd6-128">The CLR calls the `GetHostOverlappedSize` method to determine the size of the custom data that the host intends to append to the `OVERLAPPED` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bccd6-129">`GetHostOverlappedSize` je volána pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="bccd6-129">`GetHostOverlappedSize` is called only once.</span></span> <span data-ttu-id="bccd6-130">Vlastní data hostitele musí mít stejnou velikost pro každý požadavek vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="bccd6-130">The host's custom data must be the same size for every I/O request.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bccd6-131">Velikost `OVERLAPPED` samotného objektu není součástí hodnoty `pcbSize`.</span><span class="sxs-lookup"><span data-stu-id="bccd6-131">The size of the `OVERLAPPED` object itself is not included in the value of `pcbSize`.</span></span>  
  
 <span data-ttu-id="bccd6-132">Další informace o `OVERLAPPED` struktury naleznete v dokumentaci k platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="bccd6-132">For more information about the `OVERLAPPED` structure, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bccd6-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bccd6-133">Requirements</span></span>  
 <span data-ttu-id="bccd6-134">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bccd6-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bccd6-135">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bccd6-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bccd6-136">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bccd6-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bccd6-137">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bccd6-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bccd6-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bccd6-138">See also</span></span>

- <xref:System.Threading.NativeOverlapped>
- [<span data-ttu-id="bccd6-139">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bccd6-139">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="bccd6-140">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bccd6-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
