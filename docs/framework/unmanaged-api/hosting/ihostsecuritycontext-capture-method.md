---
title: "IHostSecurityContext::Capture – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityContext.Capture
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityContext::Capture
helpviewer_keywords:
- Capture method [.NET Framework hosting]
- IHostSecurityContext::Capture method [.NET Framework hosting]
ms.assetid: ae0836d0-1170-4494-bac5-d0e809df51a2
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 100ce151b81fb240434b1072be8fe8c354f85440
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsecuritycontextcapture-method"></a><span data-ttu-id="5cd3c-102">IHostSecurityContext::Capture – metoda</span><span class="sxs-lookup"><span data-stu-id="5cd3c-102">IHostSecurityContext::Capture Method</span></span>
<span data-ttu-id="5cd3c-103">Získá klon [ihostsecuritycontext –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) instance vrácená z volání [ihostsecuritymanager::getsecuritycontext –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="5cd3c-103">Gets a clone of the [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) instance returned from a call to [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cd3c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5cd3c-104">Syntax</span></span>  
  
```  
HRESULT Capture (  
    [out] IHostSecurityContext** ppClonedContext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5cd3c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5cd3c-105">Parameters</span></span>  
 `ppClonedContext`  
 <span data-ttu-id="5cd3c-106">[out] Ukazatel na adresu klon `IHostSecurityContext` objekt, který má být zaznamenány.</span><span class="sxs-lookup"><span data-stu-id="5cd3c-106">[out] A pointer to the address of a clone of the `IHostSecurityContext` object to be captured.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5cd3c-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5cd3c-107">Return Value</span></span>  
  
|<span data-ttu-id="5cd3c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5cd3c-108">HRESULT</span></span>|<span data-ttu-id="5cd3c-109">Popis</span><span class="sxs-lookup"><span data-stu-id="5cd3c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5cd3c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5cd3c-110">S_OK</span></span>|<span data-ttu-id="5cd3c-111">`Capture`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="5cd3c-111">`Capture` returned successfully.</span></span>|  
|<span data-ttu-id="5cd3c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5cd3c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5cd3c-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="5cd3c-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5cd3c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5cd3c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5cd3c-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="5cd3c-115">The call timed out.</span></span>|  
|<span data-ttu-id="5cd3c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5cd3c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5cd3c-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="5cd3c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5cd3c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5cd3c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5cd3c-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="5cd3c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5cd3c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5cd3c-120">E_FAIL</span></span>|<span data-ttu-id="5cd3c-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="5cd3c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5cd3c-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="5cd3c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5cd3c-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5cd3c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5cd3c-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5cd3c-124">Remarks</span></span>  
 <span data-ttu-id="5cd3c-125">Ukazatel rozhraní vrácená z `Capture` je klonem zaznamenané kontextu.</span><span class="sxs-lookup"><span data-stu-id="5cd3c-125">The interface pointer returned from `Capture` is a clone of the captured context.</span></span> <span data-ttu-id="5cd3c-126">Pokud tato informace se přesunou mezi bod asynchronní kódu, celé jeho životnosti je oddělená od, vůči které přišla ukazatele.</span><span class="sxs-lookup"><span data-stu-id="5cd3c-126">When this information is moved across an asynchronous code point, its lifetime is separated from that of the pointer against which the call was made.</span></span> <span data-ttu-id="5cd3c-127">Původní ukazatele proto odblokovat.</span><span class="sxs-lookup"><span data-stu-id="5cd3c-127">The original pointer can therefore be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cd3c-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5cd3c-128">Requirements</span></span>  
 <span data-ttu-id="5cd3c-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cd3c-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cd3c-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5cd3c-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5cd3c-131">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5cd3c-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5cd3c-132">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cd3c-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cd3c-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="5cd3c-133">See Also</span></span>  
 [<span data-ttu-id="5cd3c-134">Ihostsecuritycontext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5cd3c-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="5cd3c-135">Ihostsecuritymanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5cd3c-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
