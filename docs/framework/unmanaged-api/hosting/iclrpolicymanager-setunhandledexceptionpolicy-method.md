---
title: ICLRPolicyManager::SetUnhandledExceptionPolicy – metoda
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetUnhandledExceptionPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy
helpviewer_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy method [.NET Framework hosting]
- SetUnhandledExceptionPolicy method [.NET Framework hosting]
ms.assetid: 5268480e-280a-4931-b7a3-dc3ffdf7f78f
topic_type:
- apiref
ms.openlocfilehash: 7b6a4be94e526e7b464b336d221eff936808635a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120576"
---
# <a name="iclrpolicymanagersetunhandledexceptionpolicy-method"></a><span data-ttu-id="68f96-102">ICLRPolicyManager::SetUnhandledExceptionPolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="68f96-102">ICLRPolicyManager::SetUnhandledExceptionPolicy Method</span></span>
<span data-ttu-id="68f96-103">Určuje chování modulu CLR (Common Language Runtime), pokud dojde k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="68f96-103">Specifies the behavior of the common language runtime (CLR) when an unhandled exception occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68f96-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68f96-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnhandledExceptionPolicy (  
    [in] EClrUnhandledExceptionPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68f96-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="68f96-105">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="68f96-106">pro Jedna z hodnot [EClrUnhandledException –](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md) , která označuje, zda je chování nastaveno modulem CLR nebo hostitelem.</span><span class="sxs-lookup"><span data-stu-id="68f96-106">[in] One of the [EClrUnhandledException](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md) values, indicating whether the behavior is set by the CLR or the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="68f96-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="68f96-107">Return Value</span></span>  
  
|<span data-ttu-id="68f96-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="68f96-108">HRESULT</span></span>|<span data-ttu-id="68f96-109">Popis</span><span class="sxs-lookup"><span data-stu-id="68f96-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="68f96-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="68f96-110">S_OK</span></span>|<span data-ttu-id="68f96-111">`SetUnhandledExceptionPolicy` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="68f96-111">`SetUnhandledExceptionPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="68f96-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="68f96-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="68f96-113">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="68f96-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="68f96-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="68f96-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="68f96-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="68f96-115">The call timed out.</span></span>|  
|<span data-ttu-id="68f96-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="68f96-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="68f96-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="68f96-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="68f96-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="68f96-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="68f96-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="68f96-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="68f96-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="68f96-120">E_FAIL</span></span>|<span data-ttu-id="68f96-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="68f96-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="68f96-122">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="68f96-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="68f96-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="68f96-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68f96-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="68f96-124">Remarks</span></span>  
 <span data-ttu-id="68f96-125">Ve výchozím nastavení je CLR koncovou obslužnou rutinou pro všechny neošetřené výjimky a jeho výchozím chováním je odtrhnout proces.</span><span class="sxs-lookup"><span data-stu-id="68f96-125">By default, the CLR is the final handler for all unhandled exceptions, and its default behavior is to tear down the process.</span></span> <span data-ttu-id="68f96-126">Hostitel může toto chování změnit nastavením `policy` hodnoty na eHostDeterminedPolicy.</span><span class="sxs-lookup"><span data-stu-id="68f96-126">The host can change this behavior by setting the `policy` value to eHostDeterminedPolicy.</span></span> <span data-ttu-id="68f96-127">Tato hodnota umožňuje hostiteli implementovat své vlastní výchozí chování, jako u starších verzí modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="68f96-127">This value allows the host to implement its own default behavior, as with earlier versions of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68f96-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="68f96-128">Requirements</span></span>  
 <span data-ttu-id="68f96-129">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68f96-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68f96-130">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="68f96-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="68f96-131">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="68f96-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="68f96-132">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68f96-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68f96-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="68f96-133">See also</span></span>

- [<span data-ttu-id="68f96-134">EClrUnhandledException – výčet</span><span class="sxs-lookup"><span data-stu-id="68f96-134">EClrUnhandledException Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md)
- [<span data-ttu-id="68f96-135">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="68f96-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="68f96-136">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="68f96-136">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="68f96-137">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="68f96-137">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
