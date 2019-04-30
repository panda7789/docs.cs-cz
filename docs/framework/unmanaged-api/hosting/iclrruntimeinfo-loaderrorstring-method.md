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
ms.openlocfilehash: b485811b0e7d2f657ff2d2c1d7a2aa135e48a335
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771667"
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="f7688-102">ICLRRuntimeInfo::LoadErrorString – metoda</span><span class="sxs-lookup"><span data-stu-id="f7688-102">ICLRRuntimeInfo::LoadErrorString Method</span></span>
<span data-ttu-id="f7688-103">Převede hodnotu HRESULT na příslušnou chybovou zprávu pro zadanou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="f7688-103">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="f7688-104">Tato metoda nahrazuje následující funkce:</span><span class="sxs-lookup"><span data-stu-id="f7688-104">This method supersedes the following functions:</span></span>  
  
- [<span data-ttu-id="f7688-105">LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="f7688-105">LoadStringRC</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
  
- [<span data-ttu-id="f7688-106">LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="f7688-106">LoadStringRCEx</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="f7688-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7688-107">Syntax</span></span>  
  
```  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7688-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="f7688-108">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="f7688-109">[in] Hodnota HRESULT pro převod.</span><span class="sxs-lookup"><span data-stu-id="f7688-109">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="f7688-110">[out] Řetězec zprávy přidružené k dané HRESULT.</span><span class="sxs-lookup"><span data-stu-id="f7688-110">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="f7688-111">[out v] Velikost `pwzbuffer` , aby přetečení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="f7688-111">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="f7688-112">Pokud `pwzbuffer` má hodnotu null, `pcchBuffer` poskytuje očekávanou velikost `pwzbuffer` povolit předběžné přidělování.</span><span class="sxs-lookup"><span data-stu-id="f7688-112">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="f7688-113">[in] Identifikátor jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="f7688-113">[in] The culture identifier.</span></span> <span data-ttu-id="f7688-114">Pokud chcete použít výchozí jazykovou verzi, je nutné zadat -1.</span><span class="sxs-lookup"><span data-stu-id="f7688-114">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7688-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f7688-115">Return Value</span></span>  
 <span data-ttu-id="f7688-116">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="f7688-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f7688-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f7688-117">HRESULT</span></span>|<span data-ttu-id="f7688-118">Popis</span><span class="sxs-lookup"><span data-stu-id="f7688-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f7688-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="f7688-119">S_OK</span></span>|<span data-ttu-id="f7688-120">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="f7688-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="f7688-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="f7688-121">E_POINTER</span></span>|<span data-ttu-id="f7688-122">`pcchBuffer` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="f7688-122">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="f7688-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f7688-123">E_INVALIDARG</span></span>|<span data-ttu-id="f7688-124">`pwzBuffer` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="f7688-124">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f7688-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f7688-125">Requirements</span></span>  
 <span data-ttu-id="f7688-126">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7688-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7688-127">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="f7688-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f7688-128">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f7688-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f7688-129">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7688-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7688-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f7688-130">See also</span></span>

- [<span data-ttu-id="f7688-131">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f7688-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="f7688-132">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="f7688-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="f7688-133">Hostování</span><span class="sxs-lookup"><span data-stu-id="f7688-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
