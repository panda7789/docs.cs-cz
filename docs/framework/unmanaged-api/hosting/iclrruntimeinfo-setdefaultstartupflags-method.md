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
ms.openlocfilehash: 2996acd9678557b08fcfa543ecc7648ed639b143
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748338"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a><span data-ttu-id="2fcc1-102">ICLRRuntimeInfo::SetDefaultStartupFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="2fcc1-102">ICLRRuntimeInfo::SetDefaultStartupFlags Method</span></span>
<span data-ttu-id="2fcc1-103">Nastaví příznaky spuštění a konfigurační soubor hostitele, který se použije ke spuštění modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="2fcc1-103">Sets the startup flags and the host configuration file that will be used to start the runtime.</span></span> <span data-ttu-id="2fcc1-104">Tato metoda nahrazuje použití `startupFlags` parametr [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) a [corbindtoruntimehost –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="2fcc1-104">This method supersedes the use of the `startupFlags` parameter in the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fcc1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fcc1-105">Syntax</span></span>  
  
```cpp  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2fcc1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2fcc1-106">Parameters</span></span>  
 `dwStartupFlags`  
 <span data-ttu-id="2fcc1-107">[in] Příznaky spuštění hostitele nastavení.</span><span class="sxs-lookup"><span data-stu-id="2fcc1-107">[in] The host startup flags to set.</span></span> <span data-ttu-id="2fcc1-108">Použijte stejné příznaky jako se [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) a [corbindtoruntimehost –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="2fcc1-108">Use the same flags as with the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="2fcc1-109">[in] Cesta k adresáři souboru konfigurace hostitele nastavení.</span><span class="sxs-lookup"><span data-stu-id="2fcc1-109">[in] The directory path of the host configuration file to set.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2fcc1-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2fcc1-110">Return Value</span></span>  
 <span data-ttu-id="2fcc1-111">Tato metoda vrátí následující konkrétní HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="2fcc1-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="2fcc1-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2fcc1-112">HRESULT</span></span>|<span data-ttu-id="2fcc1-113">Popis</span><span class="sxs-lookup"><span data-stu-id="2fcc1-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2fcc1-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="2fcc1-114">S_OK</span></span>|<span data-ttu-id="2fcc1-115">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="2fcc1-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2fcc1-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2fcc1-116">Remarks</span></span>  
 <span data-ttu-id="2fcc1-117">Volání této metody by měl synchronizovat s více vlákny hostitele.</span><span class="sxs-lookup"><span data-stu-id="2fcc1-117">A multithreaded host should synchronize calls to this method.</span></span> <span data-ttu-id="2fcc1-118">V opačném případě vlákno A může volat `SetStartupFlags` metoda po dokončení volání vlákna B `SetStartupFlags` a před spuštěním podprocesu B modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="2fcc1-118">Otherwise, thread A might call the `SetStartupFlags` method after thread B completes a call to `SetStartupFlags` and before thread B starts the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fcc1-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2fcc1-119">Requirements</span></span>  
 <span data-ttu-id="2fcc1-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fcc1-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fcc1-121">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="2fcc1-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2fcc1-122">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2fcc1-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2fcc1-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fcc1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fcc1-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2fcc1-124">See also</span></span>

- [<span data-ttu-id="2fcc1-125">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2fcc1-125">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="2fcc1-126">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="2fcc1-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="2fcc1-127">Hostování</span><span class="sxs-lookup"><span data-stu-id="2fcc1-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
