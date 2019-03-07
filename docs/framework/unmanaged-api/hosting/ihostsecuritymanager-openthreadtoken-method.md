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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e3cd977b7709f48ddf9938b9882a4ecb55cd6f0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484495"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a><span data-ttu-id="5e76c-102">IHostSecurityManager::OpenThreadToken – metoda</span><span class="sxs-lookup"><span data-stu-id="5e76c-102">IHostSecurityManager::OpenThreadToken Method</span></span>
<span data-ttu-id="5e76c-103">Otevře se token přístupu přidružený k aktuálně spuštěné vlákno.</span><span class="sxs-lookup"><span data-stu-id="5e76c-103">Opens the discretionary access token associated with the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e76c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e76c-104">Syntax</span></span>  
  
```  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,   
    [in]  BOOL     bOpenAsSelf,   
    [out] HANDLE   *phThreadToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e76c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5e76c-105">Parameters</span></span>  
 `dwDesiredAccess`  
 <span data-ttu-id="5e76c-106">[in] Maska získat přístup k hodnotám, které určují požadované typy přístup k tokenu vlákna.</span><span class="sxs-lookup"><span data-stu-id="5e76c-106">[in] A mask of access values that specify the requested types of access to the thread token.</span></span> <span data-ttu-id="5e76c-107">Tyto hodnoty jsou definovány v Win32 `OpenThreadToken` funkce.</span><span class="sxs-lookup"><span data-stu-id="5e76c-107">These values are defined in the Win32 `OpenThreadToken` function.</span></span> <span data-ttu-id="5e76c-108">Požadované typy přístup jsou sloučeny s tokenu seznamu řízení přístupu (DACL) Chcete-li zjistit, jaké typy přístupu udělit nebo odepřít.</span><span class="sxs-lookup"><span data-stu-id="5e76c-108">The requested access types are reconciled against the token's discretionary access control list (DACL) to determine which types of access to grant or deny.</span></span>  
  
 `bOpenAsSelf`  
 <span data-ttu-id="5e76c-109">[in] `true` k určení, že má být provedena kontrola přístupu v kontextu zabezpečení procesu pro volajícího vlákna; `false` udává by měl provést kontroly přístupu v kontextu zabezpečení pro volající vlákno, samotného.</span><span class="sxs-lookup"><span data-stu-id="5e76c-109">[in] `true` to specify that the access check should be made using the security context of the process for the calling thread; `false` to specify that the access check should be performed using the security context for the calling thread itself.</span></span> <span data-ttu-id="5e76c-110">Pokud vlákno provádí zosobnění klienta, může být kontext zabezpečení, která procesu klienta.</span><span class="sxs-lookup"><span data-stu-id="5e76c-110">If the thread is impersonating a client, the security context can be that of a client process.</span></span>  
  
 `phThreadToken`  
 <span data-ttu-id="5e76c-111">[out] Ukazatel na nově otevřené přístupový token.</span><span class="sxs-lookup"><span data-stu-id="5e76c-111">[out] A pointer to the newly opened access token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e76c-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5e76c-112">Return Value</span></span>  
  
|<span data-ttu-id="5e76c-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5e76c-113">HRESULT</span></span>|<span data-ttu-id="5e76c-114">Popis</span><span class="sxs-lookup"><span data-stu-id="5e76c-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5e76c-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="5e76c-115">S_OK</span></span>|<span data-ttu-id="5e76c-116">`OpenThreadToken` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="5e76c-116">`OpenThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="5e76c-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5e76c-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5e76c-118">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="5e76c-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5e76c-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5e76c-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5e76c-120">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="5e76c-120">The call timed out.</span></span>|  
|<span data-ttu-id="5e76c-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5e76c-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5e76c-122">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="5e76c-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5e76c-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5e76c-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5e76c-124">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="5e76c-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5e76c-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5e76c-125">E_FAIL</span></span>|<span data-ttu-id="5e76c-126">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="5e76c-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5e76c-127">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="5e76c-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5e76c-128">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5e76c-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e76c-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5e76c-129">Remarks</span></span>  
 <span data-ttu-id="5e76c-130">`IHostSecurityManager::OpenThreadToken` se chová podobně jako odpovídající funkce Win32 se stejným názvem, s tím rozdílem, že funkci Win32 umožňuje volajícímu a zajistěte tak předání popisovač do libovolného vlákna, zatímco `IHostSecurityManager::OpenThreadToken` otevře pouze token spojené s volajícím vlákně.</span><span class="sxs-lookup"><span data-stu-id="5e76c-130">`IHostSecurityManager::OpenThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::OpenThreadToken` opens only the token associated with the calling thread.</span></span>  
  
 <span data-ttu-id="5e76c-131">`HANDLE` Typ není kompatibilní s rozhraním modelu COM, to znamená, jeho velikost je specifické pro operační systém, a vyžaduje vlastní zařazování.</span><span class="sxs-lookup"><span data-stu-id="5e76c-131">The `HANDLE` type is not COM-compliant, that is, its size is specific to the operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="5e76c-132">Proto je tento token pro použití pouze v rámci procesu mezi CLR a hostitelem.</span><span class="sxs-lookup"><span data-stu-id="5e76c-132">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e76c-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5e76c-133">Requirements</span></span>  
 <span data-ttu-id="5e76c-134">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e76c-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e76c-135">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5e76c-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5e76c-136">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5e76c-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5e76c-137">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e76c-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e76c-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5e76c-138">See also</span></span>
- [<span data-ttu-id="5e76c-139">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5e76c-139">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="5e76c-140">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5e76c-140">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
