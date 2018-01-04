---
title: "ICLRRuntimeInfo::IsStarted – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.IsStarted
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::IsStarted
helpviewer_keywords:
- IsStarted method [.NET Framework hosting]
- ICLRRuntimeInfo::IsStarted method [.NET Framework hosting]
ms.assetid: ef6f2662-323b-4534-aa82-6d1afb7b9309
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 991470ca0df3e0cf0470a8c40d3e8e4c40d96026
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfoisstarted-method"></a><span data-ttu-id="33a8d-102">ICLRRuntimeInfo::IsStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="33a8d-102">ICLRRuntimeInfo::IsStarted Method</span></span>
<span data-ttu-id="33a8d-103">Určuje, zda byla spuštěna modulu runtime (to znamená, zda [iclrruntimehost::Start – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) byla volána a proběhla úspěšně).</span><span class="sxs-lookup"><span data-stu-id="33a8d-103">Indicates whether the runtime has been started (that is, whether the [ICLRRuntimeHost::Start method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) has been called and has succeeded).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33a8d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33a8d-104">Syntax</span></span>  
  
```  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="33a8d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="33a8d-105">Parameters</span></span>  
 `pbStarted`  
 <span data-ttu-id="33a8d-106">[out] `true` Pokud tento modul runtime je spuštěn, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="33a8d-106">[out] `true` if this runtime is started; otherwise, `false`.</span></span>  
  
 `pdwStartupFlags`  
 <span data-ttu-id="33a8d-107">[out] Vrátí příznaky, které byly použity při spuštění modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="33a8d-107">[out] Returns the flags that were used to start the runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="33a8d-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="33a8d-108">Return Value</span></span>  
 <span data-ttu-id="33a8d-109">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="33a8d-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="33a8d-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="33a8d-110">HRESULT</span></span>|<span data-ttu-id="33a8d-111">Popis</span><span class="sxs-lookup"><span data-stu-id="33a8d-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="33a8d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="33a8d-112">S_OK</span></span>|<span data-ttu-id="33a8d-113">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="33a8d-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="33a8d-114">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="33a8d-114">E_NOTIMPL</span></span>|<span data-ttu-id="33a8d-115">Společné jazykové verzi modulu runtime (CLR) je starší než verze CLR v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="33a8d-115">The common language runtime (CLR) version is earlier than the CLR version in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33a8d-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="33a8d-116">Remarks</span></span>  
 <span data-ttu-id="33a8d-117">Tato metoda funguje pouze s CLR verze starší než verze CLR v [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="33a8d-117">This method does not work with CLR versions earlier than the CLR version in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33a8d-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="33a8d-118">Requirements</span></span>  
 <span data-ttu-id="33a8d-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33a8d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33a8d-120">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="33a8d-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="33a8d-121">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="33a8d-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="33a8d-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33a8d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33a8d-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="33a8d-123">See Also</span></span>  
 [<span data-ttu-id="33a8d-124">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="33a8d-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="33a8d-125">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="33a8d-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="33a8d-126">Hostování</span><span class="sxs-lookup"><span data-stu-id="33a8d-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
