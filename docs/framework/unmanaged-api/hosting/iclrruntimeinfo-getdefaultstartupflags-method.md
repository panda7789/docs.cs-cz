---
title: "ICLRRuntimeInfo::GetDefaultStartupFlags – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.GetDefaultStartupFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::GetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags method [.NET Framework hosting]
- GetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 35c2173e-3b0b-4b2a-950d-e0a01c6df052
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 73ad12e99a1ba98f6ea61775155cf1389118f754
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a><span data-ttu-id="083e2-102">ICLRRuntimeInfo::GetDefaultStartupFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="083e2-102">ICLRRuntimeInfo::GetDefaultStartupFlags Method</span></span>
<span data-ttu-id="083e2-103">Získá spuštění příznaky a hostitele konfigurační soubor, který se použije ke spuštění modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="083e2-103">Gets the startup flags and host configuration file that will be used to start the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="083e2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="083e2-104">Syntax</span></span>  
  
```  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="083e2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="083e2-105">Parameters</span></span>  
 `pdwStartupFlags`  
 <span data-ttu-id="083e2-106">[out] Ukazatel na příznaky spuštění hostitele, které jsou aktuálně nastavené.</span><span class="sxs-lookup"><span data-stu-id="083e2-106">[out] A pointer to the host startup flags that are currently set.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="083e2-107">[out] Ukazatel na cestu k adresáři aktuálního konfiguračního souboru hostitele.</span><span class="sxs-lookup"><span data-stu-id="083e2-107">[out] A pointer to the directory path of the current host configuration file.</span></span>  
  
 `pcchHostConfigFile`  
 <span data-ttu-id="083e2-108">[ve out] Na vstupu velikost `pwzHostConfigFile`, aby se zabránilo přetečení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="083e2-108">[in, out] On input, the size of `pwzHostConfigFile`, to avoid buffer overruns.</span></span> <span data-ttu-id="083e2-109">Pokud `pwzHostConfigFile` je null, vrátí metoda požadovaná velikost `pwzHostConfigFile` pro předběžné přidělení.</span><span class="sxs-lookup"><span data-stu-id="083e2-109">If `pwzHostConfigFile` is null, the method returns the required size of `pwzHostConfigFile` for pre-allocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="083e2-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="083e2-110">Return Value</span></span>  
 <span data-ttu-id="083e2-111">Tato metoda vrátí následující konkrétní HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="083e2-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="083e2-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="083e2-112">HRESULT</span></span>|<span data-ttu-id="083e2-113">Popis</span><span class="sxs-lookup"><span data-stu-id="083e2-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="083e2-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="083e2-114">S_OK</span></span>|<span data-ttu-id="083e2-115">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="083e2-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="083e2-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="083e2-116">Remarks</span></span>  
 <span data-ttu-id="083e2-117">Tato metoda vrátí příznak výchozí hodnoty (`STARTUP_CONCURRENT_GC` a `NULL`), nebo hodnoty od předchozího volání [iclrruntimeinfo::setdefaultstartupflags – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), nebo s hodnotami nastavenými v některé z `CorBind*` metody, pokud je vázána na tento modul runtime.</span><span class="sxs-lookup"><span data-stu-id="083e2-117">This method returns the default flag values (`STARTUP_CONCURRENT_GC` and `NULL`), or the values provided by a previous call to the [ICLRRuntimeInfo::SetDefaultStartupFlags method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), or the values set by any of the `CorBind*` methods if they are bound to this runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="083e2-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="083e2-118">Requirements</span></span>  
 <span data-ttu-id="083e2-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="083e2-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="083e2-120">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="083e2-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="083e2-121">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="083e2-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="083e2-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="083e2-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="083e2-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="083e2-123">See Also</span></span>  
 [<span data-ttu-id="083e2-124">Iclrruntimeinfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="083e2-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="083e2-125">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="083e2-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="083e2-126">Hostování</span><span class="sxs-lookup"><span data-stu-id="083e2-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
