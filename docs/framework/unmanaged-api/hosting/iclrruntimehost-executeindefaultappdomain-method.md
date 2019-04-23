---
title: ICLRRuntimeHost::ExecuteInDefaultAppDomain – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain method [.NET Framework hosting]
- ExecuteInDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 30b5cf9a-a762-4bd4-be12-d6c1442b78b1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1e6805dc67f7ec5ceb8c67d77462a0200b6c0317
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59205902"
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a><span data-ttu-id="9d728-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="9d728-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain Method</span></span>
<span data-ttu-id="9d728-103">Volá metodu zadané zadaného typu v zadaném spravovaná sestavení.</span><span class="sxs-lookup"><span data-stu-id="9d728-103">Calls the specified method of the specified type in the specified managed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d728-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d728-104">Syntax</span></span>  
  
```  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,   
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d728-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d728-105">Parameters</span></span>  
 `pwzAssemblyPath`  
 <span data-ttu-id="9d728-106">[in] Cesta k <xref:System.Reflection.Assembly> , který definuje <xref:System.Type> jehož metoda má být vyvolána.</span><span class="sxs-lookup"><span data-stu-id="9d728-106">[in] The path to the <xref:System.Reflection.Assembly> that defines the <xref:System.Type> whose method is to be invoked.</span></span>  
  
 `pwzTypeName`  
 <span data-ttu-id="9d728-107">[in] Název <xref:System.Type> , který definuje metodu, který má být vyvolán.</span><span class="sxs-lookup"><span data-stu-id="9d728-107">[in] The name of the <xref:System.Type> that defines the method to invoke.</span></span>  
  
 `pwzMethodName`  
 <span data-ttu-id="9d728-108">[in] Název metody, která se má vyvolat.</span><span class="sxs-lookup"><span data-stu-id="9d728-108">[in] The name of the method to invoke.</span></span>  
  
 `pwzArgument`  
 <span data-ttu-id="9d728-109">[in] Parametr řetězec předat metodě.</span><span class="sxs-lookup"><span data-stu-id="9d728-109">[in] The string parameter to pass to the method.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="9d728-110">[out] Celé číslo hodnoty vrácené volanou metodu.</span><span class="sxs-lookup"><span data-stu-id="9d728-110">[out] The integer value returned by the invoked method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d728-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9d728-111">Return Value</span></span>  
  
|<span data-ttu-id="9d728-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9d728-112">HRESULT</span></span>|<span data-ttu-id="9d728-113">Popis</span><span class="sxs-lookup"><span data-stu-id="9d728-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9d728-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="9d728-114">S_OK</span></span>|<span data-ttu-id="9d728-115">`ExecuteInDefaultAppDomain` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="9d728-115">`ExecuteInDefaultAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="9d728-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9d728-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9d728-117">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="9d728-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9d728-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9d728-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9d728-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="9d728-119">The call timed out.</span></span>|  
|<span data-ttu-id="9d728-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9d728-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9d728-121">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="9d728-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9d728-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9d728-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9d728-123">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="9d728-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9d728-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9d728-124">E_FAIL</span></span>|<span data-ttu-id="9d728-125">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="9d728-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9d728-126">Pokud metoda vrátí E_FAIL, seznam CRL už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="9d728-126">If a method returns E_FAIL, the CRL is no longer usable within the process.</span></span> <span data-ttu-id="9d728-127">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9d728-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d728-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9d728-128">Remarks</span></span>  
 <span data-ttu-id="9d728-129">Vyvolaná metoda musí mít následující podpis:</span><span class="sxs-lookup"><span data-stu-id="9d728-129">The invoked method must have the following signature:</span></span>  
  
```  
static int pwzMethodName (String pwzArgument)  
```  
  
 <span data-ttu-id="9d728-130">kde `pwzMethodName` představuje název volanou metodu a `pwzArgument` představuje řetězcová hodnota předaná této metodě jako parametr.</span><span class="sxs-lookup"><span data-stu-id="9d728-130">where `pwzMethodName` represents the name of the invoked method, and `pwzArgument` represents the string value passed as a parameter to that method.</span></span> <span data-ttu-id="9d728-131">Pokud hodnota HRESULT je nastavena na hodnotu S_OK, `pReturnValue` je nastavena na celočíselnou hodnotu vrácenou příkazem volanou metodu.</span><span class="sxs-lookup"><span data-stu-id="9d728-131">If the HRESULT value is set to S_OK, `pReturnValue` is set to the integer value returned by the invoked method.</span></span> <span data-ttu-id="9d728-132">V opačném případě `pReturnValue` není nastaven.</span><span class="sxs-lookup"><span data-stu-id="9d728-132">Otherwise, `pReturnValue` is not set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d728-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9d728-133">Requirements</span></span>  
 <span data-ttu-id="9d728-134">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d728-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d728-135">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9d728-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9d728-136">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9d728-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d728-137">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d728-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d728-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d728-138">See also</span></span>

- [<span data-ttu-id="9d728-139">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d728-139">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
