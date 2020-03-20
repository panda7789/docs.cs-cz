---
title: IHostSecurityManager::OpenThreadToken – metoda
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.OpenThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::OpenThreadToken
helpviewer_keywords:
- IHostSecurityManager::OpenThreadToken method [.NET Framework hosting]
- OpenThreadToken method [.NET Framework hosting]
ms.assetid: d5999052-8bf0-4a9e-8621-da6284406b18
topic_type:
- apiref
ms.openlocfilehash: 11d042ea9eecc8d428761da6eaa15f7c2907ebd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176263"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a><span data-ttu-id="b2438-102">IHostSecurityManager::OpenThreadToken – metoda</span><span class="sxs-lookup"><span data-stu-id="b2438-102">IHostSecurityManager::OpenThreadToken Method</span></span>
<span data-ttu-id="b2438-103">Otevře diskreční přístupový token přidružený k aktuálně spuštěnépodprocesu.</span><span class="sxs-lookup"><span data-stu-id="b2438-103">Opens the discretionary access token associated with the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2438-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2438-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,
    [in]  BOOL     bOpenAsSelf,
    [out] HANDLE   *phThreadToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2438-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b2438-105">Parameters</span></span>  
 `dwDesiredAccess`  
 <span data-ttu-id="b2438-106">[v] Maska přístupových hodnot, které určují požadované typy přístupu k tokenu vlákna.</span><span class="sxs-lookup"><span data-stu-id="b2438-106">[in] A mask of access values that specify the requested types of access to the thread token.</span></span> <span data-ttu-id="b2438-107">Tyto hodnoty jsou definovány `OpenThreadToken` ve funkci Win32.</span><span class="sxs-lookup"><span data-stu-id="b2438-107">These values are defined in the Win32 `OpenThreadToken` function.</span></span> <span data-ttu-id="b2438-108">Požadované typy přístupu jsou odsouhlaseny proti seznamu volitelného řízení přístupu tokenu (DACL) k určení, které typy přístupu k udělení nebo zamítnutí.</span><span class="sxs-lookup"><span data-stu-id="b2438-108">The requested access types are reconciled against the token's discretionary access control list (DACL) to determine which types of access to grant or deny.</span></span>  
  
 `bOpenAsSelf`  
 <span data-ttu-id="b2438-109">[v] `true` upřesnit, že kontrola přístupu by měla být provedena pomocí kontextu zabezpečení procesu pro volající vlákno; `false` určit, že kontrola přístupu by měla být provedena pomocí kontextu zabezpečení pro volající vlákno samotné.</span><span class="sxs-lookup"><span data-stu-id="b2438-109">[in] `true` to specify that the access check should be made using the security context of the process for the calling thread; `false` to specify that the access check should be performed using the security context for the calling thread itself.</span></span> <span data-ttu-id="b2438-110">Pokud vlákno je zosobnění klienta, kontext zabezpečení může být, že klientského procesu.</span><span class="sxs-lookup"><span data-stu-id="b2438-110">If the thread is impersonating a client, the security context can be that of a client process.</span></span>  
  
 `phThreadToken`  
 <span data-ttu-id="b2438-111">[out] Ukazatel na nově otevřený přístupový token.</span><span class="sxs-lookup"><span data-stu-id="b2438-111">[out] A pointer to the newly opened access token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2438-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b2438-112">Return Value</span></span>  
  
|<span data-ttu-id="b2438-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b2438-113">HRESULT</span></span>|<span data-ttu-id="b2438-114">Popis</span><span class="sxs-lookup"><span data-stu-id="b2438-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b2438-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="b2438-115">S_OK</span></span>|<span data-ttu-id="b2438-116">`OpenThreadToken`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="b2438-116">`OpenThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="b2438-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b2438-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b2438-118">Běžný jazyk runtime (CLR) nebyl načten do procesu nebo CLR je ve stavu, ve kterém nelze spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="b2438-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b2438-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b2438-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b2438-120">Časový čas hovoru byl vypován.</span><span class="sxs-lookup"><span data-stu-id="b2438-120">The call timed out.</span></span>|  
|<span data-ttu-id="b2438-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b2438-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b2438-122">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="b2438-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b2438-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b2438-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b2438-124">Událost byla zrušena, zatímco na ní čekalo blokované vlákno nebo vlákno.</span><span class="sxs-lookup"><span data-stu-id="b2438-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b2438-125">E_fail</span><span class="sxs-lookup"><span data-stu-id="b2438-125">E_FAIL</span></span>|<span data-ttu-id="b2438-126">Došlo k neznámému katastrofickému selhání.</span><span class="sxs-lookup"><span data-stu-id="b2438-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b2438-127">Když metoda vrátí E_FAIL CLR již není použitelný v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="b2438-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b2438-128">Následná volání metod hostování vrátí HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b2438-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2438-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b2438-129">Remarks</span></span>  
 <span data-ttu-id="b2438-130">`IHostSecurityManager::OpenThreadToken`chová podobně jako odpovídající Win32 funkce se stejným názvem, s tím rozdílem, že Win32 funkce umožňuje `IHostSecurityManager::OpenThreadToken` volajícímu předat popisovač libovolné vlákno, zatímco otevře pouze token přidružený k volající vlákno.</span><span class="sxs-lookup"><span data-stu-id="b2438-130">`IHostSecurityManager::OpenThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::OpenThreadToken` opens only the token associated with the calling thread.</span></span>  
  
 <span data-ttu-id="b2438-131">Typ `HANDLE` není kompatibilní s com, to znamená, že jeho velikost je specifická pro operační systém a vyžaduje vlastní zařazování.</span><span class="sxs-lookup"><span data-stu-id="b2438-131">The `HANDLE` type is not COM-compliant, that is, its size is specific to the operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="b2438-132">Proto tento token je určen pro použití pouze v rámci procesu, mezi CLR a hostitele.</span><span class="sxs-lookup"><span data-stu-id="b2438-132">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2438-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b2438-133">Requirements</span></span>  
 <span data-ttu-id="b2438-134">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2438-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2438-135">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b2438-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b2438-136">**Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b2438-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b2438-137">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2438-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2438-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2438-138">See also</span></span>

- [<span data-ttu-id="b2438-139">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b2438-139">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="b2438-140">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b2438-140">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
