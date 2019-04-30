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
ms.openlocfilehash: 9c39ad4638c7db45c481bd3dfccb0a82759397aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771745"
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a><span data-ttu-id="44e1d-102">ICLRRuntimeInfo::GetDefaultStartupFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="44e1d-102">ICLRRuntimeInfo::GetDefaultStartupFlags Method</span></span>
<span data-ttu-id="44e1d-103">Získá příznaky spuštění a konfiguračním souboru hostitele, který se použije ke spuštění modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="44e1d-103">Gets the startup flags and host configuration file that will be used to start the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44e1d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44e1d-104">Syntax</span></span>  
  
```  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44e1d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="44e1d-105">Parameters</span></span>  
 `pdwStartupFlags`  
 <span data-ttu-id="44e1d-106">[out] Ukazatel na příznaky spuštění hostitele, které jsou aktuálně nastaveny.</span><span class="sxs-lookup"><span data-stu-id="44e1d-106">[out] A pointer to the host startup flags that are currently set.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="44e1d-107">[out] Ukazatel na cestu k adresáři aktuálního konfiguračního souboru hostitele.</span><span class="sxs-lookup"><span data-stu-id="44e1d-107">[out] A pointer to the directory path of the current host configuration file.</span></span>  
  
 `pcchHostConfigFile`  
 <span data-ttu-id="44e1d-108">[out v] Na vstupní velikost `pwzHostConfigFile`předešli přetečení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="44e1d-108">[in, out] On input, the size of `pwzHostConfigFile`, to avoid buffer overruns.</span></span> <span data-ttu-id="44e1d-109">Pokud `pwzHostConfigFile` je null, vrátí metoda požadovaná velikost `pwzHostConfigFile` pro předběžné přidělení.</span><span class="sxs-lookup"><span data-stu-id="44e1d-109">If `pwzHostConfigFile` is null, the method returns the required size of `pwzHostConfigFile` for pre-allocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44e1d-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="44e1d-110">Return Value</span></span>  
 <span data-ttu-id="44e1d-111">Tato metoda vrátí následující konkrétní HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="44e1d-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="44e1d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="44e1d-112">HRESULT</span></span>|<span data-ttu-id="44e1d-113">Popis</span><span class="sxs-lookup"><span data-stu-id="44e1d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="44e1d-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="44e1d-114">S_OK</span></span>|<span data-ttu-id="44e1d-115">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="44e1d-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44e1d-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="44e1d-116">Remarks</span></span>  
 <span data-ttu-id="44e1d-117">Tato metoda vrátí výchozí hodnoty příznak (`STARTUP_CONCURRENT_GC` a `NULL`), nebo hodnoty poskytnuté předchozí volání [iclrruntimeinfo::setdefaultstartupflags – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), nebo hodnoty nastavené podle těchto sloupců `CorBind*` metody, pokud jsou vázány na tento modul runtime.</span><span class="sxs-lookup"><span data-stu-id="44e1d-117">This method returns the default flag values (`STARTUP_CONCURRENT_GC` and `NULL`), or the values provided by a previous call to the [ICLRRuntimeInfo::SetDefaultStartupFlags method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), or the values set by any of the `CorBind*` methods if they are bound to this runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44e1d-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="44e1d-118">Requirements</span></span>  
 <span data-ttu-id="44e1d-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44e1d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44e1d-120">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="44e1d-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="44e1d-121">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="44e1d-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="44e1d-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44e1d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44e1d-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="44e1d-123">See also</span></span>

- [<span data-ttu-id="44e1d-124">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="44e1d-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="44e1d-125">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="44e1d-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="44e1d-126">Hostování</span><span class="sxs-lookup"><span data-stu-id="44e1d-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
