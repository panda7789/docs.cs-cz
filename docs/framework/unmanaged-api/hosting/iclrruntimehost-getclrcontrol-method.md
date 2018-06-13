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
ms.openlocfilehash: 86858d5fe5bf9ac07a91e810599c27a479141f4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435052"
---
# <a name="iclrruntimehostgetclrcontrol-method"></a><span data-ttu-id="2978b-102">ICLRRuntimeHost::GetCLRControl – metoda</span><span class="sxs-lookup"><span data-stu-id="2978b-102">ICLRRuntimeHost::GetCLRControl Method</span></span>
<span data-ttu-id="2978b-103">Získá ukazatele rozhraní typu [iclrcontrol – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) , hostitelů můžete přizpůsobit aspekty common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="2978b-103">Gets an interface pointer of type [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2978b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2978b-104">Syntax</span></span>  
  
```  
HRESULT GetCLRControl(  
    [out] ICLRControl** pCLRControl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2978b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2978b-105">Parameters</span></span>  
 `pCLRControl`  
 <span data-ttu-id="2978b-106">[out] Ukazatele rozhraní typu [iclrcontrol – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) , umožňuje hostitelům nakonfigurovat další aspekty modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="2978b-106">[out] An interface pointer of type [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that enables hosts to configure additional aspects of the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2978b-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2978b-107">Return Value</span></span>  
  
|<span data-ttu-id="2978b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2978b-108">HRESULT</span></span>|<span data-ttu-id="2978b-109">Popis</span><span class="sxs-lookup"><span data-stu-id="2978b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2978b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2978b-110">S_OK</span></span>|<span data-ttu-id="2978b-111">`GetCLRControl` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="2978b-111">`GetCLRControl` returned successfully.</span></span>|  
|<span data-ttu-id="2978b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2978b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2978b-113">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="2978b-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2978b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2978b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2978b-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="2978b-115">The call timed out.</span></span>|  
|<span data-ttu-id="2978b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2978b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2978b-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="2978b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2978b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2978b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2978b-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="2978b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2978b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2978b-120">E_FAIL</span></span>|<span data-ttu-id="2978b-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="2978b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2978b-122">Pokud metoda vrátí E_FAIL, modul CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="2978b-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2978b-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2978b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2978b-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="2978b-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="2978b-125">Modul CLR již byla spuštěna.</span><span class="sxs-lookup"><span data-stu-id="2978b-125">The CLR has already started.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2978b-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2978b-126">Remarks</span></span>  
 <span data-ttu-id="2978b-127">`ICLRControl` poskytuje [getclrmanager – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metodu, která umožňuje hostiteli získání ukazatele rozhraní na jeden z typů správce.</span><span class="sxs-lookup"><span data-stu-id="2978b-127">`ICLRControl` provides the [GetCLRManager Method](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method, which enables the host to get an interface pointer to one of the manager types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2978b-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2978b-128">Requirements</span></span>  
 <span data-ttu-id="2978b-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2978b-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2978b-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2978b-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2978b-131">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2978b-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2978b-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2978b-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2978b-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="2978b-133">See Also</span></span>  
 [<span data-ttu-id="2978b-134">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2978b-134">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="2978b-135">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2978b-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
