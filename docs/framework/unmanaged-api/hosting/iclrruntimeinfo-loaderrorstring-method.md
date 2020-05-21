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
ms.openlocfilehash: da6efae38cd70a68feea56b12e86be23fde7f0cb
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762185"
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="9b689-102">ICLRRuntimeInfo::LoadErrorString – metoda</span><span class="sxs-lookup"><span data-stu-id="9b689-102">ICLRRuntimeInfo::LoadErrorString Method</span></span>
<span data-ttu-id="9b689-103">Přeloží hodnotu HRESULT do příslušné chybové zprávy pro zadanou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="9b689-103">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="9b689-104">Tato metoda nahrazuje následující funkce:</span><span class="sxs-lookup"><span data-stu-id="9b689-104">This method supersedes the following functions:</span></span>  
  
- [<span data-ttu-id="9b689-105">LoadStringRC –</span><span class="sxs-lookup"><span data-stu-id="9b689-105">LoadStringRC</span></span>](loadstringrc-function.md)  
  
- [<span data-ttu-id="9b689-106">LoadStringRCEx –</span><span class="sxs-lookup"><span data-stu-id="9b689-106">LoadStringRCEx</span></span>](loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="9b689-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b689-107">Syntax</span></span>  
  
```cpp  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b689-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="9b689-108">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="9b689-109">pro Hodnota HRESULT pro překlad.</span><span class="sxs-lookup"><span data-stu-id="9b689-109">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="9b689-110">mimo Řetězec zprávy přidružený k danému HRESULT.</span><span class="sxs-lookup"><span data-stu-id="9b689-110">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="9b689-111">[in, out] Velikost, `pwzbuffer` která se má vyhnout přetečení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="9b689-111">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="9b689-112">Pokud `pwzbuffer` má hodnotu null, `pcchBuffer` poskytuje očekávanou velikost pro povolení předběžného `pwzbuffer` přidělení.</span><span class="sxs-lookup"><span data-stu-id="9b689-112">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="9b689-113">pro Identifikátor jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="9b689-113">[in] The culture identifier.</span></span> <span data-ttu-id="9b689-114">Chcete-li použít výchozí jazykovou verzi, je nutné zadat-1.</span><span class="sxs-lookup"><span data-stu-id="9b689-114">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9b689-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9b689-115">Return Value</span></span>  
 <span data-ttu-id="9b689-116">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="9b689-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9b689-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9b689-117">HRESULT</span></span>|<span data-ttu-id="9b689-118">Popis</span><span class="sxs-lookup"><span data-stu-id="9b689-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9b689-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="9b689-119">S_OK</span></span>|<span data-ttu-id="9b689-120">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="9b689-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="9b689-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="9b689-121">E_POINTER</span></span>|<span data-ttu-id="9b689-122">`pcchBuffer`má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="9b689-122">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="9b689-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="9b689-123">E_INVALIDARG</span></span>|<span data-ttu-id="9b689-124">`pwzBuffer`má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="9b689-124">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9b689-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9b689-125">Requirements</span></span>  
 <span data-ttu-id="9b689-126">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b689-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b689-127">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="9b689-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9b689-128">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9b689-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9b689-129">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b689-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b689-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="9b689-130">See also</span></span>

- [<span data-ttu-id="9b689-131">ICLRRuntimeInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9b689-131">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="9b689-132">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="9b689-132">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="9b689-133">Hostování</span><span class="sxs-lookup"><span data-stu-id="9b689-133">Hosting</span></span>](index.md)
