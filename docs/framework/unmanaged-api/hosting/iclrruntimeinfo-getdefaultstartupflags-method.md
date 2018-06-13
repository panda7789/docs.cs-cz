---
title: ICLRRuntimeInfo::GetDefaultStartupFlags – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags method [.NET Framework hosting]
- GetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 35c2173e-3b0b-4b2a-950d-e0a01c6df052
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 546a26306a1faaeceb1337b79bd2d27970d9f5be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434210"
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a><span data-ttu-id="ad770-102">ICLRRuntimeInfo::GetDefaultStartupFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="ad770-102">ICLRRuntimeInfo::GetDefaultStartupFlags Method</span></span>
<span data-ttu-id="ad770-103">Získá spuštění příznaky a hostitele konfigurační soubor, který se použije ke spuštění modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="ad770-103">Gets the startup flags and host configuration file that will be used to start the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad770-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad770-104">Syntax</span></span>  
  
```  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ad770-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad770-105">Parameters</span></span>  
 `pdwStartupFlags`  
 <span data-ttu-id="ad770-106">[out] Ukazatel na příznaky spuštění hostitele, které jsou aktuálně nastavené.</span><span class="sxs-lookup"><span data-stu-id="ad770-106">[out] A pointer to the host startup flags that are currently set.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="ad770-107">[out] Ukazatel na cestu k adresáři aktuálního konfiguračního souboru hostitele.</span><span class="sxs-lookup"><span data-stu-id="ad770-107">[out] A pointer to the directory path of the current host configuration file.</span></span>  
  
 `pcchHostConfigFile`  
 <span data-ttu-id="ad770-108">[ve out] Na vstupu velikost `pwzHostConfigFile`, aby se zabránilo přetečení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="ad770-108">[in, out] On input, the size of `pwzHostConfigFile`, to avoid buffer overruns.</span></span> <span data-ttu-id="ad770-109">Pokud `pwzHostConfigFile` je null, vrátí metoda požadovaná velikost `pwzHostConfigFile` pro předběžné přidělení.</span><span class="sxs-lookup"><span data-stu-id="ad770-109">If `pwzHostConfigFile` is null, the method returns the required size of `pwzHostConfigFile` for pre-allocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad770-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ad770-110">Return Value</span></span>  
 <span data-ttu-id="ad770-111">Tato metoda vrátí následující konkrétní HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="ad770-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ad770-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ad770-112">HRESULT</span></span>|<span data-ttu-id="ad770-113">Popis</span><span class="sxs-lookup"><span data-stu-id="ad770-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ad770-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="ad770-114">S_OK</span></span>|<span data-ttu-id="ad770-115">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="ad770-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad770-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ad770-116">Remarks</span></span>  
 <span data-ttu-id="ad770-117">Tato metoda vrátí příznak výchozí hodnoty (`STARTUP_CONCURRENT_GC` a `NULL`), nebo hodnoty od předchozího volání [iclrruntimeinfo::setdefaultstartupflags – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), nebo s hodnotami nastavenými v některé z `CorBind*` metody, pokud je vázána na tento modul runtime.</span><span class="sxs-lookup"><span data-stu-id="ad770-117">This method returns the default flag values (`STARTUP_CONCURRENT_GC` and `NULL`), or the values provided by a previous call to the [ICLRRuntimeInfo::SetDefaultStartupFlags method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), or the values set by any of the `CorBind*` methods if they are bound to this runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad770-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ad770-118">Requirements</span></span>  
 <span data-ttu-id="ad770-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad770-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad770-120">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ad770-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ad770-121">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ad770-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ad770-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad770-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad770-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="ad770-123">See Also</span></span>  
 [<span data-ttu-id="ad770-124">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ad770-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="ad770-125">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="ad770-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="ad770-126">Hostování</span><span class="sxs-lookup"><span data-stu-id="ad770-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
