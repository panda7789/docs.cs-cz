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
ms.openlocfilehash: d021eb2d8da8c85fe538f0c73527876482429718
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656879"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a><span data-ttu-id="94af5-102">ICLRRuntimeInfo::SetDefaultStartupFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="94af5-102">ICLRRuntimeInfo::SetDefaultStartupFlags Method</span></span>
<span data-ttu-id="94af5-103">Nastaví příznaky spuštění a konfigurační soubor hostitele, který se použije ke spuštění modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="94af5-103">Sets the startup flags and the host configuration file that will be used to start the runtime.</span></span> <span data-ttu-id="94af5-104">Tato metoda nahrazuje použití `startupFlags` parametr [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) a [corbindtoruntimehost –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="94af5-104">This method supersedes the use of the `startupFlags` parameter in the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94af5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94af5-105">Syntax</span></span>  
  
```  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="94af5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="94af5-106">Parameters</span></span>  
 `dwStartupFlags`  
 <span data-ttu-id="94af5-107">[in] Příznaky spuštění hostitele nastavení.</span><span class="sxs-lookup"><span data-stu-id="94af5-107">[in] The host startup flags to set.</span></span> <span data-ttu-id="94af5-108">Použijte stejné příznaky jako se [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) a [corbindtoruntimehost –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="94af5-108">Use the same flags as with the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="94af5-109">[in] Cesta k adresáři souboru konfigurace hostitele nastavení.</span><span class="sxs-lookup"><span data-stu-id="94af5-109">[in] The directory path of the host configuration file to set.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="94af5-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="94af5-110">Return Value</span></span>  
 <span data-ttu-id="94af5-111">Tato metoda vrátí následující konkrétní HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="94af5-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="94af5-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="94af5-112">HRESULT</span></span>|<span data-ttu-id="94af5-113">Popis</span><span class="sxs-lookup"><span data-stu-id="94af5-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="94af5-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="94af5-114">S_OK</span></span>|<span data-ttu-id="94af5-115">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="94af5-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94af5-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="94af5-116">Remarks</span></span>  
 <span data-ttu-id="94af5-117">Volání této metody by měl synchronizovat s více vlákny hostitele.</span><span class="sxs-lookup"><span data-stu-id="94af5-117">A multithreaded host should synchronize calls to this method.</span></span> <span data-ttu-id="94af5-118">V opačném případě vlákno A může volat `SetStartupFlags` metoda po dokončení volání vlákna B `SetStartupFlags` a před spuštěním podprocesu B modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="94af5-118">Otherwise, thread A might call the `SetStartupFlags` method after thread B completes a call to `SetStartupFlags` and before thread B starts the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94af5-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="94af5-119">Requirements</span></span>  
 <span data-ttu-id="94af5-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94af5-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94af5-121">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="94af5-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="94af5-122">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="94af5-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="94af5-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94af5-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94af5-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94af5-124">See also</span></span>
- [<span data-ttu-id="94af5-125">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="94af5-125">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="94af5-126">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="94af5-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="94af5-127">Hostování</span><span class="sxs-lookup"><span data-stu-id="94af5-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
