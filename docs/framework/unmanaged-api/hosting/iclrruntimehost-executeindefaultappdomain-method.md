---
title: "ICLRRuntimeHost::ExecuteInDefaultAppDomain – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.ExecuteInDefaultAppDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::ExecuteInDefaultAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain method [.NET Framework hosting]
- ExecuteInDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 30b5cf9a-a762-4bd4-be12-d6c1442b78b1
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ae0e006cdaa983fd7a3c9f650b61d4579aeaf0ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a><span data-ttu-id="f6ee3-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="f6ee3-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain Method</span></span>
<span data-ttu-id="f6ee3-103">Volá metodu zadané zadaného typu v zadaném spravované sestavení.</span><span class="sxs-lookup"><span data-stu-id="f6ee3-103">Calls the specified method of the specified type in the specified managed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6ee3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6ee3-104">Syntax</span></span>  
  
```  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,   
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f6ee3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6ee3-105">Parameters</span></span>  
 `pwzAssemblyPath`  
 <span data-ttu-id="f6ee3-106">[v] Cesta k <xref:System.Reflection.Assembly> , který definuje <xref:System.Type> jehož metoda má být vyvolána.</span><span class="sxs-lookup"><span data-stu-id="f6ee3-106">[in] The path to the <xref:System.Reflection.Assembly> that defines the <xref:System.Type> whose method is to be invoked.</span></span>  
  
 `pwzTypeName`  
 <span data-ttu-id="f6ee3-107">[v] Název <xref:System.Type> , který definuje metoda k vyvolání.</span><span class="sxs-lookup"><span data-stu-id="f6ee3-107">[in] The name of the <xref:System.Type> that defines the method to invoke.</span></span>  
  
 `pwzMethodName`  
 <span data-ttu-id="f6ee3-108">[v] Název metody vyvolání.</span><span class="sxs-lookup"><span data-stu-id="f6ee3-108">[in] The name of the method to invoke.</span></span>  
  
 `pwzArgument`  
 <span data-ttu-id="f6ee3-109">[v] Parametr řetězce, které mají být předány metodě.</span><span class="sxs-lookup"><span data-stu-id="f6ee3-109">[in] The string parameter to pass to the method.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="f6ee3-110">[out] Celé číslo hodnoty vrácené volanou metodu.</span><span class="sxs-lookup"><span data-stu-id="f6ee3-110">[out] The integer value returned by the invoked method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f6ee3-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f6ee3-111">Return Value</span></span>  
  
|<span data-ttu-id="f6ee3-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f6ee3-112">HRESULT</span></span>|<span data-ttu-id="f6ee3-113">Popis</span><span class="sxs-lookup"><span data-stu-id="f6ee3-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f6ee3-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="f6ee3-114">S_OK</span></span>|<span data-ttu-id="f6ee3-115">`ExecuteInDefaultAppDomain`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="f6ee3-115">`ExecuteInDefaultAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="f6ee3-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f6ee3-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f6ee3-117">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="f6ee3-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f6ee3-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f6ee3-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f6ee3-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="f6ee3-119">The call timed out.</span></span>|  
|<span data-ttu-id="f6ee3-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f6ee3-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f6ee3-121">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="f6ee3-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f6ee3-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f6ee3-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f6ee3-123">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="f6ee3-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f6ee3-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f6ee3-124">E_FAIL</span></span>|<span data-ttu-id="f6ee3-125">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="f6ee3-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f6ee3-126">Pokud metoda vrátí E_FAIL, seznam CRL již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="f6ee3-126">If a method returns E_FAIL, the CRL is no longer usable within the process.</span></span> <span data-ttu-id="f6ee3-127">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f6ee3-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6ee3-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f6ee3-128">Remarks</span></span>  
 <span data-ttu-id="f6ee3-129">Vyvolaná metoda musí mít následující podpis:</span><span class="sxs-lookup"><span data-stu-id="f6ee3-129">The invoked method must have the following signature:</span></span>  
  
```  
static int pwzMethodName (String pwzArgument)  
```  
  
 <span data-ttu-id="f6ee3-130">kde `pwzMethodName` představuje název vyvolanou metodu a `pwzArgument` představuje hodnotu řetězce, jako parametr předaný dané metody.</span><span class="sxs-lookup"><span data-stu-id="f6ee3-130">where `pwzMethodName` represents the name of the invoked method, and `pwzArgument` represents the string value passed as a parameter to that method.</span></span> <span data-ttu-id="f6ee3-131">Pokud hodnota HRESULT nastavena na S_OK, `pReturnValue` nastavena na celé číslo hodnoty vrácené volanou metodu.</span><span class="sxs-lookup"><span data-stu-id="f6ee3-131">If the HRESULT value is set to S_OK, `pReturnValue` is set to the integer value returned by the invoked method.</span></span> <span data-ttu-id="f6ee3-132">V opačném `pReturnValue` není nastaven.</span><span class="sxs-lookup"><span data-stu-id="f6ee3-132">Otherwise, `pReturnValue` is not set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6ee3-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f6ee3-133">Requirements</span></span>  
 <span data-ttu-id="f6ee3-134">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6ee3-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6ee3-135">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f6ee3-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f6ee3-136">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f6ee3-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f6ee3-137">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6ee3-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6ee3-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="f6ee3-138">See Also</span></span>  
 [<span data-ttu-id="f6ee3-139">Iclrruntimehost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f6ee3-139">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
