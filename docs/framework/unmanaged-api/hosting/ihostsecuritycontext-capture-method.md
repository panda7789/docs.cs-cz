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
ms.openlocfilehash: aff8fa88fe811d5a07ea8ffb1653e403338ba546
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440184"
---
# <a name="ihostsecuritycontextcapture-method"></a><span data-ttu-id="c5057-102">IHostSecurityContext::Capture – metoda</span><span class="sxs-lookup"><span data-stu-id="c5057-102">IHostSecurityContext::Capture Method</span></span>
<span data-ttu-id="c5057-103">Získá klon [ihostsecuritycontext –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) instance vrácená z volání [ihostsecuritymanager::getsecuritycontext –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="c5057-103">Gets a clone of the [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) instance returned from a call to [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5057-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5057-104">Syntax</span></span>  
  
```  
HRESULT Capture (  
    [out] IHostSecurityContext** ppClonedContext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5057-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5057-105">Parameters</span></span>  
 `ppClonedContext`  
 <span data-ttu-id="c5057-106">[out] Ukazatel na adresu klon `IHostSecurityContext` objekt, který má být zaznamenány.</span><span class="sxs-lookup"><span data-stu-id="c5057-106">[out] A pointer to the address of a clone of the `IHostSecurityContext` object to be captured.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c5057-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c5057-107">Return Value</span></span>  
  
|<span data-ttu-id="c5057-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c5057-108">HRESULT</span></span>|<span data-ttu-id="c5057-109">Popis</span><span class="sxs-lookup"><span data-stu-id="c5057-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c5057-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c5057-110">S_OK</span></span>|<span data-ttu-id="c5057-111">`Capture` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="c5057-111">`Capture` returned successfully.</span></span>|  
|<span data-ttu-id="c5057-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c5057-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c5057-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c5057-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c5057-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c5057-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c5057-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="c5057-115">The call timed out.</span></span>|  
|<span data-ttu-id="c5057-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c5057-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c5057-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="c5057-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c5057-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c5057-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c5057-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="c5057-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c5057-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c5057-120">E_FAIL</span></span>|<span data-ttu-id="c5057-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="c5057-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c5057-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="c5057-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c5057-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c5057-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5057-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c5057-124">Remarks</span></span>  
 <span data-ttu-id="c5057-125">Ukazatel rozhraní vrácená z `Capture` je klonem zaznamenané kontextu.</span><span class="sxs-lookup"><span data-stu-id="c5057-125">The interface pointer returned from `Capture` is a clone of the captured context.</span></span> <span data-ttu-id="c5057-126">Pokud tato informace se přesunou mezi bod asynchronní kódu, celé jeho životnosti je oddělená od, vůči které přišla ukazatele.</span><span class="sxs-lookup"><span data-stu-id="c5057-126">When this information is moved across an asynchronous code point, its lifetime is separated from that of the pointer against which the call was made.</span></span> <span data-ttu-id="c5057-127">Původní ukazatele proto odblokovat.</span><span class="sxs-lookup"><span data-stu-id="c5057-127">The original pointer can therefore be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5057-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c5057-128">Requirements</span></span>  
 <span data-ttu-id="c5057-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5057-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5057-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c5057-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c5057-131">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c5057-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5057-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5057-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5057-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="c5057-133">See Also</span></span>  
 [<span data-ttu-id="c5057-134">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c5057-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="c5057-135">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c5057-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
