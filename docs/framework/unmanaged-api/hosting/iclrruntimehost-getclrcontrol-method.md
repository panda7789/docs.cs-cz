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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f426bac735c780d63b75eeaf49151651fd2fa65
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54692896"
---
# <a name="iclrruntimehostgetclrcontrol-method"></a><span data-ttu-id="a0577-102">ICLRRuntimeHost::GetCLRControl – metoda</span><span class="sxs-lookup"><span data-stu-id="a0577-102">ICLRRuntimeHost::GetCLRControl Method</span></span>
<span data-ttu-id="a0577-103">Získá ukazatel rozhraní typu [iclrcontrol – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) , hostitelů můžete použít k přizpůsobení aspekty modulu common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="a0577-103">Gets an interface pointer of type [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0577-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0577-104">Syntax</span></span>  
  
```  
HRESULT GetCLRControl(  
    [out] ICLRControl** pCLRControl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0577-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a0577-105">Parameters</span></span>  
 `pCLRControl`  
 <span data-ttu-id="a0577-106">[out] Ukazatel rozhraní typu [iclrcontrol – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) , která umožňuje hostitelům konfigurovat další aspekty modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="a0577-106">[out] An interface pointer of type [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that enables hosts to configure additional aspects of the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0577-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a0577-107">Return Value</span></span>  
  
|<span data-ttu-id="a0577-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a0577-108">HRESULT</span></span>|<span data-ttu-id="a0577-109">Popis</span><span class="sxs-lookup"><span data-stu-id="a0577-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a0577-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a0577-110">S_OK</span></span>|<span data-ttu-id="a0577-111">`GetCLRControl` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="a0577-111">`GetCLRControl` returned successfully.</span></span>|  
|<span data-ttu-id="a0577-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a0577-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a0577-113">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="a0577-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a0577-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a0577-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a0577-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="a0577-115">The call timed out.</span></span>|  
|<span data-ttu-id="a0577-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a0577-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a0577-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="a0577-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a0577-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a0577-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a0577-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="a0577-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a0577-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a0577-120">E_FAIL</span></span>|<span data-ttu-id="a0577-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="a0577-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a0577-122">Pokud metoda vrátí E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="a0577-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a0577-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a0577-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a0577-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="a0577-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="a0577-125">Modul CLR je již spuštěna.</span><span class="sxs-lookup"><span data-stu-id="a0577-125">The CLR has already started.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0577-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a0577-126">Remarks</span></span>  
 <span data-ttu-id="a0577-127">`ICLRControl` poskytuje [getclrmanager – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metodu, která umožňuje hostiteli zjistit ukazatel rozhraní na jeden z typů správce.</span><span class="sxs-lookup"><span data-stu-id="a0577-127">`ICLRControl` provides the [GetCLRManager Method](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method, which enables the host to get an interface pointer to one of the manager types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0577-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a0577-128">Requirements</span></span>  
 <span data-ttu-id="a0577-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0577-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0577-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a0577-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a0577-131">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a0577-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a0577-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0577-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0577-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a0577-133">See also</span></span>
- [<span data-ttu-id="a0577-134">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a0577-134">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="a0577-135">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a0577-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
