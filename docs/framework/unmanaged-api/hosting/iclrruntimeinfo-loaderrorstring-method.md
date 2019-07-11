---
title: ICLRRuntimeInfo::LoadErrorString – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.LoadErrorString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::LoadErrorString
helpviewer_keywords:
- ICLRRuntimeInfo::LoadErrorString method [.NET Framework hosting]
- LoadErrorString method [.NET Framework hosting]
ms.assetid: 52c543ab-9ef5-4ee7-b836-c0ffc35cd45b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e6638f731b335ba7552379cdc77fa912a1def4d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748372"
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="1267d-102">ICLRRuntimeInfo::LoadErrorString – metoda</span><span class="sxs-lookup"><span data-stu-id="1267d-102">ICLRRuntimeInfo::LoadErrorString Method</span></span>
<span data-ttu-id="1267d-103">Převede hodnotu HRESULT na příslušnou chybovou zprávu pro zadanou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="1267d-103">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="1267d-104">Tato metoda nahrazuje následující funkce:</span><span class="sxs-lookup"><span data-stu-id="1267d-104">This method supersedes the following functions:</span></span>  
  
- [<span data-ttu-id="1267d-105">LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="1267d-105">LoadStringRC</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
  
- [<span data-ttu-id="1267d-106">LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="1267d-106">LoadStringRCEx</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="1267d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1267d-107">Syntax</span></span>  
  
```cpp  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1267d-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="1267d-108">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="1267d-109">[in] Hodnota HRESULT pro převod.</span><span class="sxs-lookup"><span data-stu-id="1267d-109">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="1267d-110">[out] Řetězec zprávy přidružené k dané HRESULT.</span><span class="sxs-lookup"><span data-stu-id="1267d-110">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="1267d-111">[out v] Velikost `pwzbuffer` , aby přetečení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="1267d-111">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="1267d-112">Pokud `pwzbuffer` má hodnotu null, `pcchBuffer` poskytuje očekávanou velikost `pwzbuffer` povolit předběžné přidělování.</span><span class="sxs-lookup"><span data-stu-id="1267d-112">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="1267d-113">[in] Identifikátor jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="1267d-113">[in] The culture identifier.</span></span> <span data-ttu-id="1267d-114">Pokud chcete použít výchozí jazykovou verzi, je nutné zadat -1.</span><span class="sxs-lookup"><span data-stu-id="1267d-114">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1267d-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1267d-115">Return Value</span></span>  
 <span data-ttu-id="1267d-116">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="1267d-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="1267d-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1267d-117">HRESULT</span></span>|<span data-ttu-id="1267d-118">Popis</span><span class="sxs-lookup"><span data-stu-id="1267d-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1267d-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="1267d-119">S_OK</span></span>|<span data-ttu-id="1267d-120">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="1267d-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="1267d-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="1267d-121">E_POINTER</span></span>|<span data-ttu-id="1267d-122">`pcchBuffer` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="1267d-122">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="1267d-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="1267d-123">E_INVALIDARG</span></span>|<span data-ttu-id="1267d-124">`pwzBuffer` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="1267d-124">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1267d-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1267d-125">Requirements</span></span>  
 <span data-ttu-id="1267d-126">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1267d-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1267d-127">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="1267d-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1267d-128">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1267d-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1267d-129">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1267d-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1267d-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1267d-130">See also</span></span>

- [<span data-ttu-id="1267d-131">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1267d-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="1267d-132">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="1267d-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="1267d-133">Hostování</span><span class="sxs-lookup"><span data-stu-id="1267d-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
