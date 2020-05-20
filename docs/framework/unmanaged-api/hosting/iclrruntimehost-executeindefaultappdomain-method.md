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
ms.openlocfilehash: 070c52258b66dcc352f2beef81b9a0694b8301ce
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703283"
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a><span data-ttu-id="6bcfc-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="6bcfc-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain Method</span></span>
<span data-ttu-id="6bcfc-103">Volá zadanou metodu zadaného typu v zadaném spravovaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="6bcfc-103">Calls the specified method of the specified type in the specified managed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bcfc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6bcfc-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bcfc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6bcfc-105">Parameters</span></span>  
 `pwzAssemblyPath`  
 <span data-ttu-id="6bcfc-106">pro Cesta k <xref:System.Reflection.Assembly> definující, kde má <xref:System.Type> být vyvolána metoda.</span><span class="sxs-lookup"><span data-stu-id="6bcfc-106">[in] The path to the <xref:System.Reflection.Assembly> that defines the <xref:System.Type> whose method is to be invoked.</span></span>  
  
 `pwzTypeName`  
 <span data-ttu-id="6bcfc-107">pro Název <xref:System.Type> , který definuje metodu, která má být vyvolána.</span><span class="sxs-lookup"><span data-stu-id="6bcfc-107">[in] The name of the <xref:System.Type> that defines the method to invoke.</span></span>  
  
 `pwzMethodName`  
 <span data-ttu-id="6bcfc-108">pro Název metody, která se má vyvolat.</span><span class="sxs-lookup"><span data-stu-id="6bcfc-108">[in] The name of the method to invoke.</span></span>  
  
 `pwzArgument`  
 <span data-ttu-id="6bcfc-109">pro Řetězcový parametr, který se má předat metodě.</span><span class="sxs-lookup"><span data-stu-id="6bcfc-109">[in] The string parameter to pass to the method.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="6bcfc-110">mimo Celočíselná hodnota vrácená vyvolanou metodou.</span><span class="sxs-lookup"><span data-stu-id="6bcfc-110">[out] The integer value returned by the invoked method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6bcfc-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6bcfc-111">Return Value</span></span>  
  
|<span data-ttu-id="6bcfc-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6bcfc-112">HRESULT</span></span>|<span data-ttu-id="6bcfc-113">Popis</span><span class="sxs-lookup"><span data-stu-id="6bcfc-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6bcfc-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="6bcfc-114">S_OK</span></span>|<span data-ttu-id="6bcfc-115">`ExecuteInDefaultAppDomain`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="6bcfc-115">`ExecuteInDefaultAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="6bcfc-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6bcfc-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6bcfc-117">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="6bcfc-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6bcfc-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6bcfc-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6bcfc-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="6bcfc-119">The call timed out.</span></span>|  
|<span data-ttu-id="6bcfc-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6bcfc-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6bcfc-121">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="6bcfc-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6bcfc-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6bcfc-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6bcfc-123">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="6bcfc-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6bcfc-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6bcfc-124">E_FAIL</span></span>|<span data-ttu-id="6bcfc-125">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="6bcfc-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6bcfc-126">Pokud metoda vrátí E_FAIL, seznam CRL již nebude v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="6bcfc-126">If a method returns E_FAIL, the CRL is no longer usable within the process.</span></span> <span data-ttu-id="6bcfc-127">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6bcfc-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6bcfc-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6bcfc-128">Remarks</span></span>  
 <span data-ttu-id="6bcfc-129">Vyvolaná metoda musí mít následující signaturu:</span><span class="sxs-lookup"><span data-stu-id="6bcfc-129">The invoked method must have the following signature:</span></span>  
  
```cpp  
static int pwzMethodName (String pwzArgument)  
```  
  
 <span data-ttu-id="6bcfc-130">kde `pwzMethodName` představuje název vyvolané metody a `pwzArgument` představuje řetězcovou hodnotu předanou jako parametr této metodě.</span><span class="sxs-lookup"><span data-stu-id="6bcfc-130">where `pwzMethodName` represents the name of the invoked method, and `pwzArgument` represents the string value passed as a parameter to that method.</span></span> <span data-ttu-id="6bcfc-131">Pokud je hodnota HRESULT nastavena na S_OK, `pReturnValue` je nastavena na celočíselnou hodnotu vrácenou vyvolanou metodou.</span><span class="sxs-lookup"><span data-stu-id="6bcfc-131">If the HRESULT value is set to S_OK, `pReturnValue` is set to the integer value returned by the invoked method.</span></span> <span data-ttu-id="6bcfc-132">V opačném případě není `pReturnValue` nastavena.</span><span class="sxs-lookup"><span data-stu-id="6bcfc-132">Otherwise, `pReturnValue` is not set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bcfc-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6bcfc-133">Requirements</span></span>  
 <span data-ttu-id="6bcfc-134">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bcfc-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bcfc-135">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6bcfc-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6bcfc-136">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6bcfc-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6bcfc-137">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bcfc-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bcfc-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="6bcfc-138">See also</span></span>

- [<span data-ttu-id="6bcfc-139">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6bcfc-139">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
