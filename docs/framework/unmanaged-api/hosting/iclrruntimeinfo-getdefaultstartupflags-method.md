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
ms.openlocfilehash: 8513787f48ae89632816face386bbcda20555dac
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703881"
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a><span data-ttu-id="7eb44-102">ICLRRuntimeInfo::GetDefaultStartupFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="7eb44-102">ICLRRuntimeInfo::GetDefaultStartupFlags Method</span></span>
<span data-ttu-id="7eb44-103">Získá spouštěcí příznaky a konfigurační soubor hostitele, který se použije ke spuštění modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="7eb44-103">Gets the startup flags and host configuration file that will be used to start the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7eb44-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7eb44-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7eb44-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7eb44-105">Parameters</span></span>  
 `pdwStartupFlags`  
 <span data-ttu-id="7eb44-106">mimo Ukazatel na příznaky spouštění hostitele, které jsou aktuálně nastaveny.</span><span class="sxs-lookup"><span data-stu-id="7eb44-106">[out] A pointer to the host startup flags that are currently set.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="7eb44-107">mimo Ukazatel na cestu k adresáři aktuálního konfiguračního souboru hostitele.</span><span class="sxs-lookup"><span data-stu-id="7eb44-107">[out] A pointer to the directory path of the current host configuration file.</span></span>  
  
 `pcchHostConfigFile`  
 <span data-ttu-id="7eb44-108">[in, out] V případě vstupu velikost `pwzHostConfigFile` , aby nedošlo k přetečení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="7eb44-108">[in, out] On input, the size of `pwzHostConfigFile`, to avoid buffer overruns.</span></span> <span data-ttu-id="7eb44-109">Pokud `pwzHostConfigFile` je null, metoda vrátí požadovanou velikost `pwzHostConfigFile` pro předběžné přidělení.</span><span class="sxs-lookup"><span data-stu-id="7eb44-109">If `pwzHostConfigFile` is null, the method returns the required size of `pwzHostConfigFile` for pre-allocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7eb44-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7eb44-110">Return Value</span></span>  
 <span data-ttu-id="7eb44-111">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="7eb44-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7eb44-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7eb44-112">HRESULT</span></span>|<span data-ttu-id="7eb44-113">Popis</span><span class="sxs-lookup"><span data-stu-id="7eb44-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7eb44-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="7eb44-114">S_OK</span></span>|<span data-ttu-id="7eb44-115">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="7eb44-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7eb44-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7eb44-116">Remarks</span></span>  
 <span data-ttu-id="7eb44-117">Tato metoda vrátí výchozí hodnoty příznaků ( `STARTUP_CONCURRENT_GC` a `NULL` ) nebo hodnoty poskytnuté předchozím voláním [metody ICLRRuntimeInfo:: SetDefaultStartupFlags –](iclrruntimeinfo-setdefaultstartupflags-method.md)nebo hodnoty nastavené pomocí kterékoli z `CorBind*` metod, pokud jsou svázány s tímto modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="7eb44-117">This method returns the default flag values (`STARTUP_CONCURRENT_GC` and `NULL`), or the values provided by a previous call to the [ICLRRuntimeInfo::SetDefaultStartupFlags method](iclrruntimeinfo-setdefaultstartupflags-method.md), or the values set by any of the `CorBind*` methods if they are bound to this runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7eb44-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7eb44-118">Requirements</span></span>  
 <span data-ttu-id="7eb44-119">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7eb44-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7eb44-120">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="7eb44-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7eb44-121">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7eb44-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7eb44-122">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7eb44-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7eb44-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="7eb44-123">See also</span></span>

- [<span data-ttu-id="7eb44-124">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7eb44-124">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="7eb44-125">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="7eb44-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="7eb44-126">Hostování</span><span class="sxs-lookup"><span data-stu-id="7eb44-126">Hosting</span></span>](index.md)
