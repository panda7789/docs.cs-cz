---
title: ICLRRuntimeHost::GetCLRControl – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.GetCLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::GetCLRControl
helpviewer_keywords:
- ICLRRuntimeHost::GetCLRControl method [.NET Framework hosting]
- GetCLRControl method [.NET Framework hosting]
ms.assetid: e47e3655-efd5-4572-a1dc-50c69bf2a468
topic_type:
- apiref
ms.openlocfilehash: 68bcdc33e34075cc5876ee721ef57282cdaa6e86
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703681"
---
# <a name="iclrruntimehostgetclrcontrol-method"></a><span data-ttu-id="8f799-102">ICLRRuntimeHost::GetCLRControl – metoda</span><span class="sxs-lookup"><span data-stu-id="8f799-102">ICLRRuntimeHost::GetCLRControl Method</span></span>
<span data-ttu-id="8f799-103">Načte ukazatel rozhraní typu [rozhraní ICLRControl](iclrcontrol-interface.md) , které mohou hostitelé použít k přizpůsobení aspektů modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="8f799-103">Gets an interface pointer of type [ICLRControl Interface](iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f799-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f799-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCLRControl(  
    [out] ICLRControl** pCLRControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f799-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8f799-105">Parameters</span></span>  
 `pCLRControl`  
 <span data-ttu-id="8f799-106">mimo Ukazatel rozhraní typu [rozhraní ICLRControl](iclrcontrol-interface.md) , který umožňuje hostitelům konfigurovat další aspekty CLR.</span><span class="sxs-lookup"><span data-stu-id="8f799-106">[out] An interface pointer of type [ICLRControl Interface](iclrcontrol-interface.md) that enables hosts to configure additional aspects of the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f799-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8f799-107">Return Value</span></span>  
  
|<span data-ttu-id="8f799-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8f799-108">HRESULT</span></span>|<span data-ttu-id="8f799-109">Popis</span><span class="sxs-lookup"><span data-stu-id="8f799-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8f799-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8f799-110">S_OK</span></span>|<span data-ttu-id="8f799-111">`GetCLRControl`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="8f799-111">`GetCLRControl` returned successfully.</span></span>|  
|<span data-ttu-id="8f799-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8f799-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8f799-113">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="8f799-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8f799-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8f799-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8f799-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="8f799-115">The call timed out.</span></span>|  
|<span data-ttu-id="8f799-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8f799-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8f799-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="8f799-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8f799-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8f799-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8f799-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="8f799-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8f799-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8f799-120">E_FAIL</span></span>|<span data-ttu-id="8f799-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="8f799-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8f799-122">Pokud metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="8f799-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8f799-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8f799-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8f799-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="8f799-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="8f799-125">Modul CLR již byl spuštěn.</span><span class="sxs-lookup"><span data-stu-id="8f799-125">The CLR has already started.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f799-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8f799-126">Remarks</span></span>  
 <span data-ttu-id="8f799-127">`ICLRControl`poskytuje metodu [metody GetCLRManager –](iclrcontrol-getclrmanager-method.md) , která umožňuje hostiteli získat ukazatel rozhraní na jeden z typů správce.</span><span class="sxs-lookup"><span data-stu-id="8f799-127">`ICLRControl` provides the [GetCLRManager Method](iclrcontrol-getclrmanager-method.md) method, which enables the host to get an interface pointer to one of the manager types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f799-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8f799-128">Requirements</span></span>  
 <span data-ttu-id="8f799-129">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f799-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f799-130">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8f799-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8f799-131">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8f799-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8f799-132">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f799-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f799-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="8f799-133">See also</span></span>

- [<span data-ttu-id="8f799-134">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8f799-134">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="8f799-135">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8f799-135">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
