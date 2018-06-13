---
title: GetHistoryFileDirectory – funkce
ms.date: 03/30/2017
api_name:
- GetHistoryFileDirectory
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- GetHistoryFileDirectory
helpviewer_keywords:
- GetHistoryFileDirectory function [.NET Framework fusion]
ms.assetid: 93232222-926e-42ac-b85d-8a6d33977672
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bba40acf7bfd20897ece4de285fe7a9175be83e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431760"
---
# <a name="gethistoryfiledirectory-function"></a><span data-ttu-id="36886-102">GetHistoryFileDirectory – funkce</span><span class="sxs-lookup"><span data-stu-id="36886-102">GetHistoryFileDirectory Function</span></span>
<span data-ttu-id="36886-103">Načte cestu adresáře historie aplikace.</span><span class="sxs-lookup"><span data-stu-id="36886-103">Retrieves the path of the application history directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36886-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36886-104">Syntax</span></span>  
  
```  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="36886-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="36886-105">Parameters</span></span>  
 `wzDir`  
 <span data-ttu-id="36886-106">[out] Vyrovnávací paměť pro cestu k adresáři historie aplikace.</span><span class="sxs-lookup"><span data-stu-id="36886-106">[out] A buffer to hold the path to the application history directory.</span></span>  
  
 `pdwSize`  
 <span data-ttu-id="36886-107">[ve out] Délka vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="36886-107">[in, out] The length of the buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="36886-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="36886-108">Return Value</span></span>  
 <span data-ttu-id="36886-109">Tato metoda vrátí standardní kódy chyb COM, jak jsou definovány v souboru WinError.h vedle následující hodnoty.</span><span class="sxs-lookup"><span data-stu-id="36886-109">This method returns standard COM error codes, as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="36886-110">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="36886-110">Return code</span></span>|<span data-ttu-id="36886-111">Popis</span><span class="sxs-lookup"><span data-stu-id="36886-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="36886-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="36886-112">S_OK</span></span>|<span data-ttu-id="36886-113">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="36886-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="36886-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="36886-114">E_INVALIDARG</span></span>|<span data-ttu-id="36886-115">`wzDir` nebo `pdwSize` má hodnotu null, nebo verze řetězec je nesprávný.</span><span class="sxs-lookup"><span data-stu-id="36886-115">`wzDir` or `pdwSize` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36886-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="36886-116">Remarks</span></span>  
 <span data-ttu-id="36886-117">Při úspěšném dokončení `pdwSize` argument je nastaven na délku řetězec cesty.</span><span class="sxs-lookup"><span data-stu-id="36886-117">On successful completion, the `pdwSize` argument is set to the length of the path string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36886-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="36886-118">Requirements</span></span>  
 <span data-ttu-id="36886-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36886-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36886-120">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="36886-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="36886-121">**Knihovna:** knihovna Fusion.dll a Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="36886-121">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="36886-122">Pomocí knihovna Fusion.dll místo Mscorwks.dll zajistit, na které cílí správnou verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="36886-122">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="36886-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36886-123">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36886-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="36886-124">See Also</span></span>  
 [<span data-ttu-id="36886-125">CreateHistoryReader – funkce</span><span class="sxs-lookup"><span data-stu-id="36886-125">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 [<span data-ttu-id="36886-126">NukeDownloadedCache – funkce</span><span class="sxs-lookup"><span data-stu-id="36886-126">NukeDownloadedCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)  
 [<span data-ttu-id="36886-127">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="36886-127">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
