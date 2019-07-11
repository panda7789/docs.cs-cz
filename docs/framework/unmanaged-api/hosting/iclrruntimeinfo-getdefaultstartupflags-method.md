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
ms.openlocfilehash: aeb4c9935d5e9e4063497dd56276edfe6e62752a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765584"
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a><span data-ttu-id="ee201-102">ICLRRuntimeInfo::GetDefaultStartupFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="ee201-102">ICLRRuntimeInfo::GetDefaultStartupFlags Method</span></span>
<span data-ttu-id="ee201-103">Získá příznaky spuštění a konfiguračním souboru hostitele, který se použije ke spuštění modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="ee201-103">Gets the startup flags and host configuration file that will be used to start the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee201-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee201-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee201-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ee201-105">Parameters</span></span>  
 `pdwStartupFlags`  
 <span data-ttu-id="ee201-106">[out] Ukazatel na příznaky spuštění hostitele, které jsou aktuálně nastaveny.</span><span class="sxs-lookup"><span data-stu-id="ee201-106">[out] A pointer to the host startup flags that are currently set.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="ee201-107">[out] Ukazatel na cestu k adresáři aktuálního konfiguračního souboru hostitele.</span><span class="sxs-lookup"><span data-stu-id="ee201-107">[out] A pointer to the directory path of the current host configuration file.</span></span>  
  
 `pcchHostConfigFile`  
 <span data-ttu-id="ee201-108">[out v] Na vstupní velikost `pwzHostConfigFile`předešli přetečení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="ee201-108">[in, out] On input, the size of `pwzHostConfigFile`, to avoid buffer overruns.</span></span> <span data-ttu-id="ee201-109">Pokud `pwzHostConfigFile` je null, vrátí metoda požadovaná velikost `pwzHostConfigFile` pro předběžné přidělení.</span><span class="sxs-lookup"><span data-stu-id="ee201-109">If `pwzHostConfigFile` is null, the method returns the required size of `pwzHostConfigFile` for pre-allocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ee201-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ee201-110">Return Value</span></span>  
 <span data-ttu-id="ee201-111">Tato metoda vrátí následující konkrétní HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="ee201-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ee201-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ee201-112">HRESULT</span></span>|<span data-ttu-id="ee201-113">Popis</span><span class="sxs-lookup"><span data-stu-id="ee201-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ee201-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="ee201-114">S_OK</span></span>|<span data-ttu-id="ee201-115">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="ee201-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee201-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ee201-116">Remarks</span></span>  
 <span data-ttu-id="ee201-117">Tato metoda vrátí výchozí hodnoty příznak (`STARTUP_CONCURRENT_GC` a `NULL`), nebo hodnoty poskytnuté předchozí volání [iclrruntimeinfo::setdefaultstartupflags – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), nebo hodnoty nastavené podle těchto sloupců `CorBind*` metody, pokud jsou vázány na tento modul runtime.</span><span class="sxs-lookup"><span data-stu-id="ee201-117">This method returns the default flag values (`STARTUP_CONCURRENT_GC` and `NULL`), or the values provided by a previous call to the [ICLRRuntimeInfo::SetDefaultStartupFlags method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), or the values set by any of the `CorBind*` methods if they are bound to this runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee201-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ee201-118">Requirements</span></span>  
 <span data-ttu-id="ee201-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee201-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee201-120">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ee201-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ee201-121">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ee201-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ee201-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee201-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee201-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ee201-123">See also</span></span>

- [<span data-ttu-id="ee201-124">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ee201-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="ee201-125">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="ee201-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="ee201-126">Hostování</span><span class="sxs-lookup"><span data-stu-id="ee201-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
