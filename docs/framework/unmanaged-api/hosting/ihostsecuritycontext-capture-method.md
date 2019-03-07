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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 92b593248a7a196247a5b4c71a90cd8944665bbe
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485275"
---
# <a name="ihostsecuritycontextcapture-method"></a><span data-ttu-id="6078b-102">IHostSecurityContext::Capture – metoda</span><span class="sxs-lookup"><span data-stu-id="6078b-102">IHostSecurityContext::Capture Method</span></span>
<span data-ttu-id="6078b-103">Získá klonu [ihostsecuritycontext –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) instance vrácená z volání [ihostsecuritymanager::getsecuritycontext –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="6078b-103">Gets a clone of the [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) instance returned from a call to [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6078b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6078b-104">Syntax</span></span>  
  
```  
HRESULT Capture (  
    [out] IHostSecurityContext** ppClonedContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6078b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6078b-105">Parameters</span></span>  
 `ppClonedContext`  
 <span data-ttu-id="6078b-106">[out] Ukazatel na adresu klonu `IHostSecurityContext` objektu se dají zachytit.</span><span class="sxs-lookup"><span data-stu-id="6078b-106">[out] A pointer to the address of a clone of the `IHostSecurityContext` object to be captured.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6078b-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6078b-107">Return Value</span></span>  
  
|<span data-ttu-id="6078b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6078b-108">HRESULT</span></span>|<span data-ttu-id="6078b-109">Popis</span><span class="sxs-lookup"><span data-stu-id="6078b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6078b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6078b-110">S_OK</span></span>|<span data-ttu-id="6078b-111">`Capture` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="6078b-111">`Capture` returned successfully.</span></span>|  
|<span data-ttu-id="6078b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6078b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6078b-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="6078b-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6078b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6078b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6078b-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="6078b-115">The call timed out.</span></span>|  
|<span data-ttu-id="6078b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6078b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6078b-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="6078b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6078b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6078b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6078b-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="6078b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6078b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6078b-120">E_FAIL</span></span>|<span data-ttu-id="6078b-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="6078b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6078b-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="6078b-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6078b-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6078b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6078b-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6078b-124">Remarks</span></span>  
 <span data-ttu-id="6078b-125">Vrácený ukazatel rozhraní `Capture` je klonem zachyceném kontextu.</span><span class="sxs-lookup"><span data-stu-id="6078b-125">The interface pointer returned from `Capture` is a clone of the captured context.</span></span> <span data-ttu-id="6078b-126">Pokud tyto informace je přesouvat mezi jako bod asynchronní kód, dobu života je oddělená od, proti kterému bylo provedeno volání ukazatele.</span><span class="sxs-lookup"><span data-stu-id="6078b-126">When this information is moved across an asynchronous code point, its lifetime is separated from that of the pointer against which the call was made.</span></span> <span data-ttu-id="6078b-127">Můžete proto vydávaly původní ukazatel.</span><span class="sxs-lookup"><span data-stu-id="6078b-127">The original pointer can therefore be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6078b-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6078b-128">Requirements</span></span>  
 <span data-ttu-id="6078b-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6078b-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6078b-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6078b-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6078b-131">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6078b-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6078b-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6078b-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6078b-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6078b-133">See also</span></span>
- [<span data-ttu-id="6078b-134">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6078b-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="6078b-135">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6078b-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
