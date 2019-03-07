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
ms.openlocfilehash: 440f2f7c542c697b3d817c988211303c60073979
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492356"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a><span data-ttu-id="5ab91-102">ICLRRuntimeInfo::SetDefaultStartupFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="5ab91-102">ICLRRuntimeInfo::SetDefaultStartupFlags Method</span></span>
<span data-ttu-id="5ab91-103">Nastaví příznaky spuštění a konfigurační soubor hostitele, který se použije ke spuštění modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="5ab91-103">Sets the startup flags and the host configuration file that will be used to start the runtime.</span></span> <span data-ttu-id="5ab91-104">Tato metoda nahrazuje použití `startupFlags` parametr [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) a [corbindtoruntimehost –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="5ab91-104">This method supersedes the use of the `startupFlags` parameter in the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ab91-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ab91-105">Syntax</span></span>  
  
```  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ab91-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5ab91-106">Parameters</span></span>  
 `dwStartupFlags`  
 <span data-ttu-id="5ab91-107">[in] Příznaky spuštění hostitele nastavení.</span><span class="sxs-lookup"><span data-stu-id="5ab91-107">[in] The host startup flags to set.</span></span> <span data-ttu-id="5ab91-108">Použijte stejné příznaky jako se [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) a [corbindtoruntimehost –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="5ab91-108">Use the same flags as with the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="5ab91-109">[in] Cesta k adresáři souboru konfigurace hostitele nastavení.</span><span class="sxs-lookup"><span data-stu-id="5ab91-109">[in] The directory path of the host configuration file to set.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5ab91-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5ab91-110">Return Value</span></span>  
 <span data-ttu-id="5ab91-111">Tato metoda vrátí následující konkrétní HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="5ab91-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="5ab91-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5ab91-112">HRESULT</span></span>|<span data-ttu-id="5ab91-113">Popis</span><span class="sxs-lookup"><span data-stu-id="5ab91-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5ab91-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="5ab91-114">S_OK</span></span>|<span data-ttu-id="5ab91-115">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="5ab91-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ab91-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5ab91-116">Remarks</span></span>  
 <span data-ttu-id="5ab91-117">Volání této metody by měl synchronizovat s více vlákny hostitele.</span><span class="sxs-lookup"><span data-stu-id="5ab91-117">A multithreaded host should synchronize calls to this method.</span></span> <span data-ttu-id="5ab91-118">V opačném případě vlákno A může volat `SetStartupFlags` metoda po dokončení volání vlákna B `SetStartupFlags` a před spuštěním podprocesu B modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="5ab91-118">Otherwise, thread A might call the `SetStartupFlags` method after thread B completes a call to `SetStartupFlags` and before thread B starts the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ab91-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5ab91-119">Requirements</span></span>  
 <span data-ttu-id="5ab91-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ab91-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ab91-121">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="5ab91-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5ab91-122">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5ab91-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5ab91-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ab91-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ab91-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5ab91-124">See also</span></span>
- [<span data-ttu-id="5ab91-125">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5ab91-125">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="5ab91-126">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="5ab91-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="5ab91-127">Hostování</span><span class="sxs-lookup"><span data-stu-id="5ab91-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
