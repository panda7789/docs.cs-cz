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
ms.openlocfilehash: 1a1bc7609042422de876fe167a9e61655aaf62b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176406"
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a><span data-ttu-id="8b914-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="8b914-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain Method</span></span>
<span data-ttu-id="8b914-103">Volá zadanou metodu zadaného typu v zadaném spravovaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="8b914-103">Calls the specified method of the specified type in the specified managed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b914-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b914-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b914-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b914-105">Parameters</span></span>  
 `pwzAssemblyPath`  
 <span data-ttu-id="8b914-106">[v] Cesta <xref:System.Reflection.Assembly> k, která definuje, <xref:System.Type> jehož metoda má být vyvolána.</span><span class="sxs-lookup"><span data-stu-id="8b914-106">[in] The path to the <xref:System.Reflection.Assembly> that defines the <xref:System.Type> whose method is to be invoked.</span></span>  
  
 `pwzTypeName`  
 <span data-ttu-id="8b914-107">[v] <xref:System.Type> Název, který definuje metodu vyvolat.</span><span class="sxs-lookup"><span data-stu-id="8b914-107">[in] The name of the <xref:System.Type> that defines the method to invoke.</span></span>  
  
 `pwzMethodName`  
 <span data-ttu-id="8b914-108">[v] Název metody vyvolat.</span><span class="sxs-lookup"><span data-stu-id="8b914-108">[in] The name of the method to invoke.</span></span>  
  
 `pwzArgument`  
 <span data-ttu-id="8b914-109">[v] Parametr řetězce předat metodě.</span><span class="sxs-lookup"><span data-stu-id="8b914-109">[in] The string parameter to pass to the method.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="8b914-110">[out] Hodnota celéčíslo vrácené vztažnou metodou.</span><span class="sxs-lookup"><span data-stu-id="8b914-110">[out] The integer value returned by the invoked method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b914-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8b914-111">Return Value</span></span>  
  
|<span data-ttu-id="8b914-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8b914-112">HRESULT</span></span>|<span data-ttu-id="8b914-113">Popis</span><span class="sxs-lookup"><span data-stu-id="8b914-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8b914-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="8b914-114">S_OK</span></span>|<span data-ttu-id="8b914-115">`ExecuteInDefaultAppDomain`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="8b914-115">`ExecuteInDefaultAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="8b914-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8b914-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8b914-117">Běžný jazyk runtime (CLR) nebyl načten do procesu nebo CLR je ve stavu, ve kterém nelze spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="8b914-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8b914-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8b914-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8b914-119">Časový čas hovoru byl vypován.</span><span class="sxs-lookup"><span data-stu-id="8b914-119">The call timed out.</span></span>|  
|<span data-ttu-id="8b914-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8b914-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8b914-121">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="8b914-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8b914-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8b914-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8b914-123">Událost byla zrušena, zatímco na ní čekalo blokované vlákno nebo vlákno.</span><span class="sxs-lookup"><span data-stu-id="8b914-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8b914-124">E_fail</span><span class="sxs-lookup"><span data-stu-id="8b914-124">E_FAIL</span></span>|<span data-ttu-id="8b914-125">Došlo k neznámému katastrofickému selhání.</span><span class="sxs-lookup"><span data-stu-id="8b914-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8b914-126">Pokud metoda vrátí E_FAIL, seznam odvolaných hodnot již není použitelný v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="8b914-126">If a method returns E_FAIL, the CRL is no longer usable within the process.</span></span> <span data-ttu-id="8b914-127">Následná volání metod hostování vrátí HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8b914-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b914-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8b914-128">Remarks</span></span>  
 <span data-ttu-id="8b914-129">Metoda vyvolaná musí mít následující podpis:</span><span class="sxs-lookup"><span data-stu-id="8b914-129">The invoked method must have the following signature:</span></span>  
  
```cpp  
static int pwzMethodName (String pwzArgument)  
```  
  
 <span data-ttu-id="8b914-130">kde `pwzMethodName` představuje název vztažné `pwzArgument` metody a představuje hodnotu řetězce předanou jako parametr této metodě.</span><span class="sxs-lookup"><span data-stu-id="8b914-130">where `pwzMethodName` represents the name of the invoked method, and `pwzArgument` represents the string value passed as a parameter to that method.</span></span> <span data-ttu-id="8b914-131">Pokud je hodnota HRESULT nastavena na S_OK, `pReturnValue` je nastavena na hodnotu celéčíslo vrácenou vztažnou metodou.</span><span class="sxs-lookup"><span data-stu-id="8b914-131">If the HRESULT value is set to S_OK, `pReturnValue` is set to the integer value returned by the invoked method.</span></span> <span data-ttu-id="8b914-132">V `pReturnValue` opačném případě není nastavena.</span><span class="sxs-lookup"><span data-stu-id="8b914-132">Otherwise, `pReturnValue` is not set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b914-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8b914-133">Requirements</span></span>  
 <span data-ttu-id="8b914-134">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b914-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b914-135">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8b914-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8b914-136">**Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8b914-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8b914-137">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b914-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b914-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="8b914-138">See also</span></span>

- [<span data-ttu-id="8b914-139">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8b914-139">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
