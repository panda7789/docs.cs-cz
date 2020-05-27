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
ms.openlocfilehash: 85c7308f794929d753b50f58f69168f67a31cb85
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803879"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a><span data-ttu-id="aecf4-102">IHostSecurityManager::OpenThreadToken – metoda</span><span class="sxs-lookup"><span data-stu-id="aecf4-102">IHostSecurityManager::OpenThreadToken Method</span></span>
<span data-ttu-id="aecf4-103">Otevře volitelný přístupový token přidružený k aktuálně spuštěnému vláknu.</span><span class="sxs-lookup"><span data-stu-id="aecf4-103">Opens the discretionary access token associated with the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aecf4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aecf4-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,
    [in]  BOOL     bOpenAsSelf,
    [out] HANDLE   *phThreadToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aecf4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aecf4-105">Parameters</span></span>  
 `dwDesiredAccess`  
 <span data-ttu-id="aecf4-106">pro Maska přístupových hodnot, které určují požadované typy přístupu k tokenu vlákna.</span><span class="sxs-lookup"><span data-stu-id="aecf4-106">[in] A mask of access values that specify the requested types of access to the thread token.</span></span> <span data-ttu-id="aecf4-107">Tyto hodnoty jsou definovány ve funkci Win32 `OpenThreadToken` .</span><span class="sxs-lookup"><span data-stu-id="aecf4-107">These values are defined in the Win32 `OpenThreadToken` function.</span></span> <span data-ttu-id="aecf4-108">Požadované typy přístupu jsou odsouhlaseny proti volitelnému seznamu řízení přístupu (DACL) tokenu, aby bylo možné určit, které typy přístupu udělit nebo odepřít.</span><span class="sxs-lookup"><span data-stu-id="aecf4-108">The requested access types are reconciled against the token's discretionary access control list (DACL) to determine which types of access to grant or deny.</span></span>  
  
 `bOpenAsSelf`  
 <span data-ttu-id="aecf4-109">[in] `true` Chcete-li určit, že by měla být provedena kontroly přístupu pomocí kontextu zabezpečení procesu pro volající vlákno; `false`Chcete-li určit, že by měla být provedena kontroly přístupu pomocí kontextu zabezpečení pro samotné volající vlákno.</span><span class="sxs-lookup"><span data-stu-id="aecf4-109">[in] `true` to specify that the access check should be made using the security context of the process for the calling thread; `false` to specify that the access check should be performed using the security context for the calling thread itself.</span></span> <span data-ttu-id="aecf4-110">Pokud vlákno zosobňuje klienta, může být kontextem zabezpečení klientským procesem.</span><span class="sxs-lookup"><span data-stu-id="aecf4-110">If the thread is impersonating a client, the security context can be that of a client process.</span></span>  
  
 `phThreadToken`  
 <span data-ttu-id="aecf4-111">mimo Ukazatel na nově otevřený přístupový token.</span><span class="sxs-lookup"><span data-stu-id="aecf4-111">[out] A pointer to the newly opened access token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aecf4-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="aecf4-112">Return Value</span></span>  
  
|<span data-ttu-id="aecf4-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aecf4-113">HRESULT</span></span>|<span data-ttu-id="aecf4-114">Popis</span><span class="sxs-lookup"><span data-stu-id="aecf4-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aecf4-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="aecf4-115">S_OK</span></span>|<span data-ttu-id="aecf4-116">`OpenThreadToken`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="aecf4-116">`OpenThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="aecf4-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aecf4-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aecf4-118">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="aecf4-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aecf4-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aecf4-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="aecf4-120">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="aecf4-120">The call timed out.</span></span>|  
|<span data-ttu-id="aecf4-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="aecf4-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="aecf4-122">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="aecf4-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="aecf4-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="aecf4-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="aecf4-124">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="aecf4-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="aecf4-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aecf4-125">E_FAIL</span></span>|<span data-ttu-id="aecf4-126">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="aecf4-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aecf4-127">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="aecf4-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aecf4-128">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="aecf4-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aecf4-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aecf4-129">Remarks</span></span>  
 <span data-ttu-id="aecf4-130">`IHostSecurityManager::OpenThreadToken`se chová podobně jako odpovídající funkce Win32 se stejným názvem, s tím rozdílem, že funkce Win32 umožňuje volajícímu předat popisovač do libovolného vlákna, zatímco `IHostSecurityManager::OpenThreadToken` otevře pouze token přidružený k volajícímu vláknu.</span><span class="sxs-lookup"><span data-stu-id="aecf4-130">`IHostSecurityManager::OpenThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::OpenThreadToken` opens only the token associated with the calling thread.</span></span>  
  
 <span data-ttu-id="aecf4-131">`HANDLE`Typ není kompatibilní s modelem COM, to znamená, že jeho velikost je specifická pro operační systém a vyžaduje vlastní zařazování.</span><span class="sxs-lookup"><span data-stu-id="aecf4-131">The `HANDLE` type is not COM-compliant, that is, its size is specific to the operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="aecf4-132">Proto je tento token určen pouze pro použití v rámci procesu, mezi CLR a hostitelem.</span><span class="sxs-lookup"><span data-stu-id="aecf4-132">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aecf4-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aecf4-133">Requirements</span></span>  
 <span data-ttu-id="aecf4-134">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aecf4-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aecf4-135">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="aecf4-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aecf4-136">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="aecf4-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aecf4-137">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aecf4-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aecf4-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="aecf4-138">See also</span></span>

- [<span data-ttu-id="aecf4-139">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aecf4-139">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="aecf4-140">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aecf4-140">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
