---
title: IHostSecurityContext::Capture – metoda
ms.date: 03/30/2017
api_name:
- IHostSecurityContext.Capture
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext::Capture
helpviewer_keywords:
- Capture method [.NET Framework hosting]
- IHostSecurityContext::Capture method [.NET Framework hosting]
ms.assetid: ae0836d0-1170-4494-bac5-d0e809df51a2
topic_type:
- apiref
ms.openlocfilehash: 96bb3a530bf4c63c3662ecfa635a929381fc0de6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121540"
---
# <a name="ihostsecuritycontextcapture-method"></a><span data-ttu-id="2f149-102">IHostSecurityContext::Capture – metoda</span><span class="sxs-lookup"><span data-stu-id="2f149-102">IHostSecurityContext::Capture Method</span></span>
<span data-ttu-id="2f149-103">Získá klon instance [IHostSecurityContext –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) vrácené voláním [IHostSecurityManager:: GetSecurityContext –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="2f149-103">Gets a clone of the [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) instance returned from a call to [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f149-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f149-104">Syntax</span></span>  
  
```cpp
HRESULT Capture (  
    [out] IHostSecurityContext** ppClonedContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f149-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2f149-105">Parameters</span></span>  
 `ppClonedContext`  
 <span data-ttu-id="2f149-106">mimo Ukazatel na adresu klonu objektu `IHostSecurityContext`, který se má zachytit.</span><span class="sxs-lookup"><span data-stu-id="2f149-106">[out] A pointer to the address of a clone of the `IHostSecurityContext` object to be captured.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f149-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2f149-107">Return Value</span></span>  
  
|<span data-ttu-id="2f149-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2f149-108">HRESULT</span></span>|<span data-ttu-id="2f149-109">Popis</span><span class="sxs-lookup"><span data-stu-id="2f149-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2f149-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2f149-110">S_OK</span></span>|<span data-ttu-id="2f149-111">`Capture` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="2f149-111">`Capture` returned successfully.</span></span>|  
|<span data-ttu-id="2f149-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2f149-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2f149-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="2f149-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2f149-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2f149-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2f149-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="2f149-115">The call timed out.</span></span>|  
|<span data-ttu-id="2f149-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2f149-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2f149-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="2f149-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2f149-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2f149-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2f149-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="2f149-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2f149-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2f149-120">E_FAIL</span></span>|<span data-ttu-id="2f149-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="2f149-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2f149-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="2f149-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2f149-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2f149-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f149-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2f149-124">Remarks</span></span>  
 <span data-ttu-id="2f149-125">Ukazatel rozhraní vrácený z `Capture` je klonem zachyceného kontextu.</span><span class="sxs-lookup"><span data-stu-id="2f149-125">The interface pointer returned from `Capture` is a clone of the captured context.</span></span> <span data-ttu-id="2f149-126">Pokud jsou tyto informace přesunuty v rámci asynchronního bodu kódu, jeho životnost je oddělena od objektu ukazatele, proti kterému bylo volání provedeno.</span><span class="sxs-lookup"><span data-stu-id="2f149-126">When this information is moved across an asynchronous code point, its lifetime is separated from that of the pointer against which the call was made.</span></span> <span data-ttu-id="2f149-127">Původní ukazatel lze proto uvolnit.</span><span class="sxs-lookup"><span data-stu-id="2f149-127">The original pointer can therefore be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f149-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2f149-128">Requirements</span></span>  
 <span data-ttu-id="2f149-129">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f149-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f149-130">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2f149-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2f149-131">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2f149-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2f149-132">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f149-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f149-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2f149-133">See also</span></span>

- [<span data-ttu-id="2f149-134">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f149-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="2f149-135">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f149-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
