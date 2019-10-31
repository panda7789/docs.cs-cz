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
ms.openlocfilehash: 20f2041599e85b8df20a7a9cf44680da9f17244e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195933"
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="cf9fd-102">ICLRRuntimeInfo::LoadErrorString – metoda</span><span class="sxs-lookup"><span data-stu-id="cf9fd-102">ICLRRuntimeInfo::LoadErrorString Method</span></span>
<span data-ttu-id="cf9fd-103">Přeloží hodnotu HRESULT do příslušné chybové zprávy pro zadanou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="cf9fd-103">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="cf9fd-104">Tato metoda nahrazuje následující funkce:</span><span class="sxs-lookup"><span data-stu-id="cf9fd-104">This method supersedes the following functions:</span></span>  
  
- [<span data-ttu-id="cf9fd-105">LoadStringRC –</span><span class="sxs-lookup"><span data-stu-id="cf9fd-105">LoadStringRC</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
  
- [<span data-ttu-id="cf9fd-106">LoadStringRCEx –</span><span class="sxs-lookup"><span data-stu-id="cf9fd-106">LoadStringRCEx</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="cf9fd-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf9fd-107">Syntax</span></span>  
  
```cpp  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf9fd-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="cf9fd-108">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="cf9fd-109">pro Hodnota HRESULT pro překlad.</span><span class="sxs-lookup"><span data-stu-id="cf9fd-109">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="cf9fd-110">mimo Řetězec zprávy přidružený k danému HRESULT.</span><span class="sxs-lookup"><span data-stu-id="cf9fd-110">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="cf9fd-111">[in, out] Velikost `pwzbuffer`, aby se předešlo přetečení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="cf9fd-111">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="cf9fd-112">Pokud je `pwzbuffer` null, `pcchBuffer` poskytuje očekávanou velikost `pwzbuffer` pro povolení předběžného přidělení.</span><span class="sxs-lookup"><span data-stu-id="cf9fd-112">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="cf9fd-113">pro Identifikátor jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="cf9fd-113">[in] The culture identifier.</span></span> <span data-ttu-id="cf9fd-114">Chcete-li použít výchozí jazykovou verzi, je nutné zadat-1.</span><span class="sxs-lookup"><span data-stu-id="cf9fd-114">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cf9fd-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cf9fd-115">Return Value</span></span>  
 <span data-ttu-id="cf9fd-116">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="cf9fd-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="cf9fd-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cf9fd-117">HRESULT</span></span>|<span data-ttu-id="cf9fd-118">Popis</span><span class="sxs-lookup"><span data-stu-id="cf9fd-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cf9fd-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="cf9fd-119">S_OK</span></span>|<span data-ttu-id="cf9fd-120">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="cf9fd-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="cf9fd-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="cf9fd-121">E_POINTER</span></span>|<span data-ttu-id="cf9fd-122">`pcchBuffer` je null.</span><span class="sxs-lookup"><span data-stu-id="cf9fd-122">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="cf9fd-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="cf9fd-123">E_INVALIDARG</span></span>|<span data-ttu-id="cf9fd-124">`pwzBuffer` je null.</span><span class="sxs-lookup"><span data-stu-id="cf9fd-124">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cf9fd-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cf9fd-125">Requirements</span></span>  
 <span data-ttu-id="cf9fd-126">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf9fd-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf9fd-127">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="cf9fd-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="cf9fd-128">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cf9fd-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf9fd-129">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf9fd-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf9fd-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cf9fd-130">See also</span></span>

- [<span data-ttu-id="cf9fd-131">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cf9fd-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="cf9fd-132">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="cf9fd-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="cf9fd-133">Hostování</span><span class="sxs-lookup"><span data-stu-id="cf9fd-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
