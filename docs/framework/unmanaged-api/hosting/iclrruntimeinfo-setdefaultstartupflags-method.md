---
title: ICLRRuntimeInfo::SetDefaultStartupFlags – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b0871636f816d62c1f65c74d22014d74fb1fb97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433276"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a><span data-ttu-id="fa7ea-102">ICLRRuntimeInfo::SetDefaultStartupFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="fa7ea-102">ICLRRuntimeInfo::SetDefaultStartupFlags Method</span></span>
<span data-ttu-id="fa7ea-103">Nastaví příznaky spuštění a konfiguračního souboru hostitele, který se použije ke spuštění modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="fa7ea-103">Sets the startup flags and the host configuration file that will be used to start the runtime.</span></span> <span data-ttu-id="fa7ea-104">Tato metoda nahrazuje použití `startupFlags` parametr ve [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) a [corbindtoruntimehost –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="fa7ea-104">This method supersedes the use of the `startupFlags` parameter in the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa7ea-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fa7ea-105">Syntax</span></span>  
  
```  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fa7ea-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="fa7ea-106">Parameters</span></span>  
 `dwStartupFlags`  
 <span data-ttu-id="fa7ea-107">[v] Příznaky spuštění hostitele k nastavení.</span><span class="sxs-lookup"><span data-stu-id="fa7ea-107">[in] The host startup flags to set.</span></span> <span data-ttu-id="fa7ea-108">Použít stejnou příznaky jako s [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) a [corbindtoruntimehost –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="fa7ea-108">Use the same flags as with the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="fa7ea-109">[v] Cestu k adresáři konfiguračního souboru hostitelů nastavení.</span><span class="sxs-lookup"><span data-stu-id="fa7ea-109">[in] The directory path of the host configuration file to set.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fa7ea-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fa7ea-110">Return Value</span></span>  
 <span data-ttu-id="fa7ea-111">Tato metoda vrátí následující konkrétní HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="fa7ea-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="fa7ea-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fa7ea-112">HRESULT</span></span>|<span data-ttu-id="fa7ea-113">Popis</span><span class="sxs-lookup"><span data-stu-id="fa7ea-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fa7ea-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="fa7ea-114">S_OK</span></span>|<span data-ttu-id="fa7ea-115">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="fa7ea-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa7ea-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fa7ea-116">Remarks</span></span>  
 <span data-ttu-id="fa7ea-117">Hostitel s více vlákny synchronizovat volání této metody.</span><span class="sxs-lookup"><span data-stu-id="fa7ea-117">A multithreaded host should synchronize calls to this method.</span></span> <span data-ttu-id="fa7ea-118">Jinak, může být přístup z více vláken A volání `SetStartupFlags` metoda po dokončení volání vlákno B `SetStartupFlags` a před zahájením vlákno B modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="fa7ea-118">Otherwise, thread A might call the `SetStartupFlags` method after thread B completes a call to `SetStartupFlags` and before thread B starts the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa7ea-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fa7ea-119">Requirements</span></span>  
 <span data-ttu-id="fa7ea-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa7ea-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa7ea-121">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="fa7ea-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="fa7ea-122">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fa7ea-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fa7ea-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa7ea-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa7ea-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="fa7ea-124">See Also</span></span>  
 [<span data-ttu-id="fa7ea-125">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fa7ea-125">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="fa7ea-126">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="fa7ea-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="fa7ea-127">Hostování</span><span class="sxs-lookup"><span data-stu-id="fa7ea-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
