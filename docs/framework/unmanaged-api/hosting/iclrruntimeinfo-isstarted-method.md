---
title: ICLRRuntimeInfo::IsStarted – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsStarted
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsStarted
helpviewer_keywords:
- IsStarted method [.NET Framework hosting]
- ICLRRuntimeInfo::IsStarted method [.NET Framework hosting]
ms.assetid: ef6f2662-323b-4534-aa82-6d1afb7b9309
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b09c509c3e0ba941a34f60ff522117ff30d83caf
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2019
ms.locfileid: "66457392"
---
# <a name="iclrruntimeinfoisstarted-method"></a><span data-ttu-id="a0502-102">ICLRRuntimeInfo::IsStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="a0502-102">ICLRRuntimeInfo::IsStarted Method</span></span>
<span data-ttu-id="a0502-103">Označuje, zda modul runtime byl spuštěn (to znamená, zda [ICLRRuntimeHost::Start – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) byla volána a proběhlo úspěšně).</span><span class="sxs-lookup"><span data-stu-id="a0502-103">Indicates whether the runtime has been started (that is, whether the [ICLRRuntimeHost::Start method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) has been called and has succeeded).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0502-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0502-104">Syntax</span></span>  
  
```  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0502-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a0502-105">Parameters</span></span>  
 `pbStarted`  
 <span data-ttu-id="a0502-106">[out] `true` Pokud tento modul runtime je spuštěna; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="a0502-106">[out] `true` if this runtime is started; otherwise, `false`.</span></span>  
  
 `pdwStartupFlags`  
 <span data-ttu-id="a0502-107">[out] Vrátí příznaky, které byly použity při spuštění modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="a0502-107">[out] Returns the flags that were used to start the runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0502-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a0502-108">Return Value</span></span>  
 <span data-ttu-id="a0502-109">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="a0502-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a0502-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a0502-110">HRESULT</span></span>|<span data-ttu-id="a0502-111">Popis</span><span class="sxs-lookup"><span data-stu-id="a0502-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a0502-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="a0502-112">S_OK</span></span>|<span data-ttu-id="a0502-113">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="a0502-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="a0502-114">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="a0502-114">E_NOTIMPL</span></span>|<span data-ttu-id="a0502-115">Společné jazykové verzi modulu runtime (CLR) je starší než verze CLR [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a0502-115">The common language runtime (CLR) version is earlier than the CLR version in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0502-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a0502-116">Remarks</span></span>  
 <span data-ttu-id="a0502-117">Tato metoda nebude fungovat s CLR verze starší než verze modulu CLR v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="a0502-117">This method does not work with CLR versions earlier than the CLR version in the .NET Framework 4.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0502-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a0502-118">Requirements</span></span>  
 <span data-ttu-id="a0502-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0502-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0502-120">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="a0502-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a0502-121">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a0502-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a0502-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0502-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0502-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a0502-123">See also</span></span>

- [<span data-ttu-id="a0502-124">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a0502-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="a0502-125">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="a0502-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="a0502-126">Hostování</span><span class="sxs-lookup"><span data-stu-id="a0502-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
