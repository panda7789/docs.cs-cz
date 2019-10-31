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
ms.openlocfilehash: 0ce822533b0699f3467dc08044aa4dab59285a77
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120317"
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a><span data-ttu-id="ae199-102">ICLRRuntimeInfo::GetDefaultStartupFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="ae199-102">ICLRRuntimeInfo::GetDefaultStartupFlags Method</span></span>
<span data-ttu-id="ae199-103">Získá spouštěcí příznaky a konfigurační soubor hostitele, který se použije ke spuštění modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="ae199-103">Gets the startup flags and host configuration file that will be used to start the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae199-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae199-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae199-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ae199-105">Parameters</span></span>  
 `pdwStartupFlags`  
 <span data-ttu-id="ae199-106">mimo Ukazatel na příznaky spouštění hostitele, které jsou aktuálně nastaveny.</span><span class="sxs-lookup"><span data-stu-id="ae199-106">[out] A pointer to the host startup flags that are currently set.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="ae199-107">mimo Ukazatel na cestu k adresáři aktuálního konfiguračního souboru hostitele.</span><span class="sxs-lookup"><span data-stu-id="ae199-107">[out] A pointer to the directory path of the current host configuration file.</span></span>  
  
 `pcchHostConfigFile`  
 <span data-ttu-id="ae199-108">[in, out] V případě vstupu velikost `pwzHostConfigFile`, aby se předešlo přetečení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="ae199-108">[in, out] On input, the size of `pwzHostConfigFile`, to avoid buffer overruns.</span></span> <span data-ttu-id="ae199-109">Pokud je `pwzHostConfigFile` null, metoda vrátí požadovanou velikost `pwzHostConfigFile` pro předběžné přidělení.</span><span class="sxs-lookup"><span data-stu-id="ae199-109">If `pwzHostConfigFile` is null, the method returns the required size of `pwzHostConfigFile` for pre-allocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae199-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ae199-110">Return Value</span></span>  
 <span data-ttu-id="ae199-111">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="ae199-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ae199-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ae199-112">HRESULT</span></span>|<span data-ttu-id="ae199-113">Popis</span><span class="sxs-lookup"><span data-stu-id="ae199-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ae199-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="ae199-114">S_OK</span></span>|<span data-ttu-id="ae199-115">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="ae199-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae199-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ae199-116">Remarks</span></span>  
 <span data-ttu-id="ae199-117">Tato metoda vrací výchozí hodnoty příznaků (`STARTUP_CONCURRENT_GC` a `NULL`) nebo hodnoty poskytnuté předchozím voláním [metody ICLRRuntimeInfo:: SetDefaultStartupFlags –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md)nebo hodnoty nastavené pomocí kterékoli metody `CorBind*`, pokud jsou svázány s tímto modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="ae199-117">This method returns the default flag values (`STARTUP_CONCURRENT_GC` and `NULL`), or the values provided by a previous call to the [ICLRRuntimeInfo::SetDefaultStartupFlags method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), or the values set by any of the `CorBind*` methods if they are bound to this runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae199-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ae199-118">Requirements</span></span>  
 <span data-ttu-id="ae199-119">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae199-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae199-120">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="ae199-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ae199-121">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ae199-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ae199-122">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae199-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae199-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae199-123">See also</span></span>

- [<span data-ttu-id="ae199-124">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ae199-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="ae199-125">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="ae199-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="ae199-126">Hostování</span><span class="sxs-lookup"><span data-stu-id="ae199-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
