---
title: ICLRRuntimeInfo::LoadErrorString – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 43a00d687c6a9ec42cb8573e70d181b4dc2c7d0e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433214"
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="fc2b1-102">ICLRRuntimeInfo::LoadErrorString – metoda</span><span class="sxs-lookup"><span data-stu-id="fc2b1-102">ICLRRuntimeInfo::LoadErrorString Method</span></span>
<span data-ttu-id="fc2b1-103">Změní hodnotu HRESULT na příslušná chybová zpráva pro zadanou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="fc2b1-103">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="fc2b1-104">Tato metoda nahrazuje následující funkce:</span><span class="sxs-lookup"><span data-stu-id="fc2b1-104">This method supersedes the following functions:</span></span>  
  
-   [<span data-ttu-id="fc2b1-105">Loadstringrc –</span><span class="sxs-lookup"><span data-stu-id="fc2b1-105">LoadStringRC</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
  
-   [<span data-ttu-id="fc2b1-106">Loadstringrcex –</span><span class="sxs-lookup"><span data-stu-id="fc2b1-106">LoadStringRCEx</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="fc2b1-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc2b1-107">Syntax</span></span>  
  
```  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fc2b1-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc2b1-108">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="fc2b1-109">[v] HRESULT přeložit.</span><span class="sxs-lookup"><span data-stu-id="fc2b1-109">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="fc2b1-110">[out] Zpráva řetězce spojeného s danou hodnotou HRESULT.</span><span class="sxs-lookup"><span data-stu-id="fc2b1-110">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="fc2b1-111">[ve out] Velikost `pwzbuffer` předejdete přetečení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="fc2b1-111">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="fc2b1-112">Pokud `pwzbuffer` má hodnotu null, `pcchBuffer` poskytuje očekávané velikosti `pwzbuffer` umožnit předběžné přidělování.</span><span class="sxs-lookup"><span data-stu-id="fc2b1-112">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="fc2b1-113">[v] Identifikátor jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="fc2b1-113">[in] The culture identifier.</span></span> <span data-ttu-id="fc2b1-114">Chcete-li použít výchozí jazykovou verzi, musíte zadat hodnotu -1.</span><span class="sxs-lookup"><span data-stu-id="fc2b1-114">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc2b1-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fc2b1-115">Return Value</span></span>  
 <span data-ttu-id="fc2b1-116">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="fc2b1-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="fc2b1-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fc2b1-117">HRESULT</span></span>|<span data-ttu-id="fc2b1-118">Popis</span><span class="sxs-lookup"><span data-stu-id="fc2b1-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fc2b1-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="fc2b1-119">S_OK</span></span>|<span data-ttu-id="fc2b1-120">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="fc2b1-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="fc2b1-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="fc2b1-121">E_POINTER</span></span>|<span data-ttu-id="fc2b1-122">`pcchBuffer` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="fc2b1-122">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="fc2b1-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="fc2b1-123">E_INVALIDARG</span></span>|<span data-ttu-id="fc2b1-124">`pwzBuffer` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="fc2b1-124">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fc2b1-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fc2b1-125">Requirements</span></span>  
 <span data-ttu-id="fc2b1-126">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc2b1-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc2b1-127">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="fc2b1-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="fc2b1-128">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fc2b1-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fc2b1-129">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc2b1-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc2b1-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="fc2b1-130">See Also</span></span>  
 [<span data-ttu-id="fc2b1-131">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fc2b1-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="fc2b1-132">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="fc2b1-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="fc2b1-133">Hostování</span><span class="sxs-lookup"><span data-stu-id="fc2b1-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
