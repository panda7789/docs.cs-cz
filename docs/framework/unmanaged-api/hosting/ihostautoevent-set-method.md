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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a5972ad555b6c3286777b5da79598fc7f1239b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438624"
---
# <a name="ihostautoeventset-method"></a><span data-ttu-id="9b055-102">IHostAutoEvent::Set – metoda</span><span class="sxs-lookup"><span data-stu-id="9b055-102">IHostAutoEvent::Set Method</span></span>
<span data-ttu-id="9b055-103">Nastaví aktuální [ihostautoevent –](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance do signalizovaného stavu.</span><span class="sxs-lookup"><span data-stu-id="9b055-103">Sets the current [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b055-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b055-104">Syntax</span></span>  
  
```  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9b055-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9b055-105">Return Value</span></span>  
  
|<span data-ttu-id="9b055-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9b055-106">HRESULT</span></span>|<span data-ttu-id="9b055-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9b055-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9b055-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="9b055-108">S_OK</span></span>|<span data-ttu-id="9b055-109">`Set` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="9b055-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="9b055-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9b055-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9b055-111">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="9b055-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9b055-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9b055-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9b055-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="9b055-113">The call timed out.</span></span>|  
|<span data-ttu-id="9b055-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9b055-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9b055-115">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="9b055-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9b055-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9b055-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9b055-117">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="9b055-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9b055-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9b055-118">E_FAIL</span></span>|<span data-ttu-id="9b055-119">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="9b055-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9b055-120">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="9b055-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9b055-121">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9b055-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9b055-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9b055-122">Requirements</span></span>  
 <span data-ttu-id="9b055-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b055-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b055-124">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9b055-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9b055-125">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9b055-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9b055-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b055-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b055-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="9b055-127">See Also</span></span>  
 [<span data-ttu-id="9b055-128">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9b055-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="9b055-129">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9b055-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="9b055-130">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9b055-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="9b055-131">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9b055-131">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
