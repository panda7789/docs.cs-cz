---
title: "ICLRRuntimeInfo::SetDefaultStartupFlags – metoda"
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
- ICLRRuntimeInfo.SetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags method [.NET Framework hosting]
- SetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 98ae174f-bff0-48f1-9e05-6cb63b451824
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 69306210ae4e957562d0bda88159d0506bca3877
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a><span data-ttu-id="89090-102">ICLRRuntimeInfo::SetDefaultStartupFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="89090-102">ICLRRuntimeInfo::SetDefaultStartupFlags Method</span></span>
<span data-ttu-id="89090-103">Nastaví příznaky spuštění a konfiguračního souboru hostitele, který se použije ke spuštění modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="89090-103">Sets the startup flags and the host configuration file that will be used to start the runtime.</span></span> <span data-ttu-id="89090-104">Tato metoda nahrazuje použití `startupFlags` parametr ve [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) a [corbindtoruntimehost –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="89090-104">This method supersedes the use of the `startupFlags` parameter in the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89090-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89090-105">Syntax</span></span>  
  
```  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="89090-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="89090-106">Parameters</span></span>  
 `dwStartupFlags`  
 <span data-ttu-id="89090-107">[v] Příznaky spuštění hostitele k nastavení.</span><span class="sxs-lookup"><span data-stu-id="89090-107">[in] The host startup flags to set.</span></span> <span data-ttu-id="89090-108">Použít stejnou příznaky jako s [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) a [corbindtoruntimehost –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="89090-108">Use the same flags as with the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="89090-109">[v] Cestu k adresáři konfiguračního souboru hostitelů nastavení.</span><span class="sxs-lookup"><span data-stu-id="89090-109">[in] The directory path of the host configuration file to set.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89090-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="89090-110">Return Value</span></span>  
 <span data-ttu-id="89090-111">Tato metoda vrátí následující konkrétní HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="89090-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="89090-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="89090-112">HRESULT</span></span>|<span data-ttu-id="89090-113">Popis</span><span class="sxs-lookup"><span data-stu-id="89090-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="89090-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="89090-114">S_OK</span></span>|<span data-ttu-id="89090-115">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="89090-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89090-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="89090-116">Remarks</span></span>  
 <span data-ttu-id="89090-117">Hostitel s více vlákny synchronizovat volání této metody.</span><span class="sxs-lookup"><span data-stu-id="89090-117">A multithreaded host should synchronize calls to this method.</span></span> <span data-ttu-id="89090-118">Jinak, může být přístup z více vláken A volání `SetStartupFlags` metoda po dokončení volání vlákno B `SetStartupFlags` a před zahájením vlákno B modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="89090-118">Otherwise, thread A might call the `SetStartupFlags` method after thread B completes a call to `SetStartupFlags` and before thread B starts the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89090-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="89090-119">Requirements</span></span>  
 <span data-ttu-id="89090-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89090-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89090-121">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="89090-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="89090-122">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="89090-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="89090-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89090-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89090-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="89090-124">See Also</span></span>  
 [<span data-ttu-id="89090-125">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="89090-125">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="89090-126">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="89090-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="89090-127">Hostování</span><span class="sxs-lookup"><span data-stu-id="89090-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
