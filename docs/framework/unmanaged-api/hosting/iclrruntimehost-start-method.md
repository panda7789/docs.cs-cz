---
title: ICLRRuntimeHost::Start – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::Start
helpviewer_keywords:
- ICLRRuntimeHost::Start method [.NET Framework hosting]
- Start method, ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: c0a6dce5-0a8d-42e8-808b-6ca14df9d289
topic_type:
- apiref
ms.openlocfilehash: a599e754202309a2b61d1761150f3f570fd0dc76
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120413"
---
# <a name="iclrruntimehoststart-method"></a><span data-ttu-id="cb469-102">ICLRRuntimeHost::Start – metoda</span><span class="sxs-lookup"><span data-stu-id="cb469-102">ICLRRuntimeHost::Start Method</span></span>
<span data-ttu-id="cb469-103">Inicializuje modul CLR (Common Language Runtime) na proces.</span><span class="sxs-lookup"><span data-stu-id="cb469-103">Initializes the common language runtime (CLR) into a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb469-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb469-104">Syntax</span></span>  
  
```cpp  
HRESULT Start();  
```  
  
## <a name="return-value"></a><span data-ttu-id="cb469-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cb469-105">Return Value</span></span>  
  
|<span data-ttu-id="cb469-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cb469-106">HRESULT</span></span>|<span data-ttu-id="cb469-107">Popis</span><span class="sxs-lookup"><span data-stu-id="cb469-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cb469-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="cb469-108">S_OK</span></span>|<span data-ttu-id="cb469-109">`Start` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="cb469-109">`Start` returned successfully.</span></span>|  
|<span data-ttu-id="cb469-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cb469-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cb469-111">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="cb469-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cb469-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cb469-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cb469-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="cb469-113">The call timed out.</span></span>|  
|<span data-ttu-id="cb469-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cb469-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cb469-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="cb469-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cb469-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cb469-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cb469-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="cb469-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cb469-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cb469-118">E_FAIL</span></span>|<span data-ttu-id="cb469-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="cb469-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cb469-120">Pokud metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="cb469-120">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cb469-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cb469-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb469-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cb469-122">Remarks</span></span>  
 <span data-ttu-id="cb469-123">V mnoha scénářích není nutné volat `Start`, protože modul runtime se sama inicializuje automaticky při první žádosti o spuštění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="cb469-123">In many scenarios it is not necessary to call `Start`, because the runtime will initialize itself automatically upon the first request to run managed code.</span></span> <span data-ttu-id="cb469-124">Můžete však použít `Start` k zadání přesně v případě, že by měl být inicializován modul runtime.</span><span class="sxs-lookup"><span data-stu-id="cb469-124">You can, however, use `Start` to specify exactly when the runtime should be initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb469-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cb469-125">Requirements</span></span>  
 <span data-ttu-id="cb469-126">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb469-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb469-127">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cb469-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cb469-128">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cb469-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cb469-129">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb469-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb469-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb469-130">See also</span></span>

- <xref:System.AppDomain>
- [<span data-ttu-id="cb469-131">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cb469-131">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
