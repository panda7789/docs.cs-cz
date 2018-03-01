---
title: "ICLRRuntimeInfo::LoadErrorString – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRRuntimeInfo.LoadErrorString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::LoadErrorString
helpviewer_keywords:
- ICLRRuntimeInfo::LoadErrorString method [.NET Framework hosting]
- LoadErrorString method [.NET Framework hosting]
ms.assetid: 52c543ab-9ef5-4ee7-b836-c0ffc35cd45b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d6253844e931b7b9126b2df28c7977eaa1d92d70
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="8892b-102">ICLRRuntimeInfo::LoadErrorString – metoda</span><span class="sxs-lookup"><span data-stu-id="8892b-102">ICLRRuntimeInfo::LoadErrorString Method</span></span>
<span data-ttu-id="8892b-103">Změní hodnotu HRESULT na příslušná chybová zpráva pro zadanou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="8892b-103">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="8892b-104">Tato metoda nahrazuje následující funkce:</span><span class="sxs-lookup"><span data-stu-id="8892b-104">This method supersedes the following functions:</span></span>  
  
-   [<span data-ttu-id="8892b-105">Loadstringrc –</span><span class="sxs-lookup"><span data-stu-id="8892b-105">LoadStringRC</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
  
-   [<span data-ttu-id="8892b-106">Loadstringrcex –</span><span class="sxs-lookup"><span data-stu-id="8892b-106">LoadStringRCEx</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="8892b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8892b-107">Syntax</span></span>  
  
```  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8892b-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="8892b-108">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="8892b-109">[v] HRESULT přeložit.</span><span class="sxs-lookup"><span data-stu-id="8892b-109">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="8892b-110">[out] Zpráva řetězce spojeného s danou hodnotou HRESULT.</span><span class="sxs-lookup"><span data-stu-id="8892b-110">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="8892b-111">[ve out] Velikost `pwzbuffer` předejdete přetečení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="8892b-111">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="8892b-112">Pokud `pwzbuffer` má hodnotu null, `pcchBuffer` poskytuje očekávané velikosti `pwzbuffer` umožnit předběžné přidělování.</span><span class="sxs-lookup"><span data-stu-id="8892b-112">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="8892b-113">[v] Identifikátor jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="8892b-113">[in] The culture identifier.</span></span> <span data-ttu-id="8892b-114">Chcete-li použít výchozí jazykovou verzi, musíte zadat hodnotu -1.</span><span class="sxs-lookup"><span data-stu-id="8892b-114">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8892b-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8892b-115">Return Value</span></span>  
 <span data-ttu-id="8892b-116">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="8892b-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8892b-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8892b-117">HRESULT</span></span>|<span data-ttu-id="8892b-118">Popis</span><span class="sxs-lookup"><span data-stu-id="8892b-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8892b-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="8892b-119">S_OK</span></span>|<span data-ttu-id="8892b-120">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="8892b-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="8892b-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="8892b-121">E_POINTER</span></span>|<span data-ttu-id="8892b-122">`pcchBuffer`má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="8892b-122">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="8892b-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8892b-123">E_INVALIDARG</span></span>|<span data-ttu-id="8892b-124">`pwzBuffer`má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="8892b-124">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8892b-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8892b-125">Requirements</span></span>  
 <span data-ttu-id="8892b-126">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8892b-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8892b-127">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="8892b-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8892b-128">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8892b-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8892b-129">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8892b-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8892b-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="8892b-130">See Also</span></span>  
 [<span data-ttu-id="8892b-131">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8892b-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="8892b-132">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="8892b-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="8892b-133">Hostování</span><span class="sxs-lookup"><span data-stu-id="8892b-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
