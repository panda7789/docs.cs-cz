---
title: IHostSecurityManager::RevertToSelf – metoda
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.RevertToSelf
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::RevertToSelf
helpviewer_keywords:
- RevertToSelf method [.NET Framework hosting]
- IHostSecurityManager::RevertToSelf method [.NET Framework hosting]
ms.assetid: 189f28f8-f9a1-4192-aedc-91084e4f8b99
topic_type:
- apiref
ms.openlocfilehash: 456553e4cb5a6c6a557b5c3ac677fad12a5798bf
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803820"
---
# <a name="ihostsecuritymanagerreverttoself-method"></a><span data-ttu-id="73da8-102">IHostSecurityManager::RevertToSelf – metoda</span><span class="sxs-lookup"><span data-stu-id="73da8-102">IHostSecurityManager::RevertToSelf Method</span></span>
<span data-ttu-id="73da8-103">Ukončí zosobnění identity aktuálního uživatele a vrátí původní token vlákna.</span><span class="sxs-lookup"><span data-stu-id="73da8-103">Terminates impersonation of the current user identity and returns the original thread token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73da8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73da8-104">Syntax</span></span>  
  
```cpp  
HRESULT RevertToSelf ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="73da8-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="73da8-105">Return Value</span></span>  
  
|<span data-ttu-id="73da8-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="73da8-106">HRESULT</span></span>|<span data-ttu-id="73da8-107">Popis</span><span class="sxs-lookup"><span data-stu-id="73da8-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="73da8-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="73da8-108">S_OK</span></span>|<span data-ttu-id="73da8-109">`RevertToSelf`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="73da8-109">`RevertToSelf` returned successfully.</span></span>|  
|<span data-ttu-id="73da8-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="73da8-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="73da8-111">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="73da8-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="73da8-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="73da8-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="73da8-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="73da8-113">The call timed out.</span></span>|  
|<span data-ttu-id="73da8-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="73da8-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="73da8-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="73da8-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="73da8-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="73da8-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="73da8-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="73da8-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="73da8-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="73da8-118">E_FAIL</span></span>|<span data-ttu-id="73da8-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="73da8-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="73da8-120">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="73da8-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="73da8-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="73da8-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73da8-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="73da8-122">Remarks</span></span>  
 <span data-ttu-id="73da8-123">`RevertToSelf`je volána pro návrat k původnímu tokenu vlákna po předchozím volání metody [ImpersonateLoggedOnUser –](ihostsecuritymanager-impersonateloggedonuser-method.md) .</span><span class="sxs-lookup"><span data-stu-id="73da8-123">`RevertToSelf` is called to return to the original thread token, after an earlier call to the [ImpersonateLoggedOnUser](ihostsecuritymanager-impersonateloggedonuser-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73da8-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="73da8-124">Requirements</span></span>  
 <span data-ttu-id="73da8-125">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73da8-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73da8-126">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="73da8-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="73da8-127">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="73da8-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="73da8-128">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73da8-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73da8-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="73da8-129">See also</span></span>

- [<span data-ttu-id="73da8-130">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="73da8-130">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="73da8-131">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="73da8-131">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="73da8-132">ImpersonateLoggedOnUser – metoda</span><span class="sxs-lookup"><span data-stu-id="73da8-132">ImpersonateLoggedOnUser Method</span></span>](ihostsecuritymanager-impersonateloggedonuser-method.md)
