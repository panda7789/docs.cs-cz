---
title: ICLRRuntimeHost::Stop – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.Stop
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::Stop
helpviewer_keywords:
- ICLRRuntimeHost::Stop method [.NET Framework hosting]
- Stop method, ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: b8fd7daf-8f8d-4ad7-92ae-019db244cec1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5fcadb708638efb0b7946426c538e01661505dfa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912245"
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="9e76f-102">ICLRRuntimeHost::Stop – metoda</span><span class="sxs-lookup"><span data-stu-id="9e76f-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="9e76f-103">Zastaví provádění kódu modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="9e76f-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9e76f-104">Tato metoda neuvolní prostředky do hostitele, uvolní aplikační domény nebo zničí vlákna.</span><span class="sxs-lookup"><span data-stu-id="9e76f-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="9e76f-105">Aby bylo možné uvolnit tyto prostředky, je nutné ukončit proces.</span><span class="sxs-lookup"><span data-stu-id="9e76f-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e76f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e76f-106">Syntax</span></span>  
  
```cpp  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9e76f-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9e76f-107">Return Value</span></span>  
  
|<span data-ttu-id="9e76f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9e76f-108">HRESULT</span></span>|<span data-ttu-id="9e76f-109">Popis</span><span class="sxs-lookup"><span data-stu-id="9e76f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9e76f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9e76f-110">S_OK</span></span>|<span data-ttu-id="9e76f-111">`Stop`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="9e76f-111">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="9e76f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9e76f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9e76f-113">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="9e76f-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9e76f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9e76f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9e76f-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="9e76f-115">The call timed out.</span></span>|  
|<span data-ttu-id="9e76f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9e76f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9e76f-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="9e76f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9e76f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9e76f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9e76f-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="9e76f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9e76f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9e76f-120">E_FAIL</span></span>|<span data-ttu-id="9e76f-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="9e76f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9e76f-122">Pokud metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="9e76f-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9e76f-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9e76f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9e76f-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9e76f-124">Requirements</span></span>  
 <span data-ttu-id="9e76f-125">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e76f-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e76f-126">**Hlaviček** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9e76f-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9e76f-127">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9e76f-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9e76f-128">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e76f-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e76f-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9e76f-129">See also</span></span>

- [<span data-ttu-id="9e76f-130">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9e76f-130">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
