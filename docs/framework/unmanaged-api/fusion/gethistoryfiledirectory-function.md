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
ms.openlocfilehash: b60dde31707175a27d2dc6c50484d6089adaeaa6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229615"
---
# <a name="gethistoryfiledirectory-function"></a><span data-ttu-id="89d77-102">GetHistoryFileDirectory – funkce</span><span class="sxs-lookup"><span data-stu-id="89d77-102">GetHistoryFileDirectory Function</span></span>
<span data-ttu-id="89d77-103">Načte cestu adresáře historie aplikace.</span><span class="sxs-lookup"><span data-stu-id="89d77-103">Retrieves the path of the application history directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89d77-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89d77-104">Syntax</span></span>  
  
```  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89d77-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="89d77-105">Parameters</span></span>  
 `wzDir`  
 <span data-ttu-id="89d77-106">[out] Vyrovnávací paměť pro cestu k adresáři aplikace historie.</span><span class="sxs-lookup"><span data-stu-id="89d77-106">[out] A buffer to hold the path to the application history directory.</span></span>  
  
 `pdwSize`  
 <span data-ttu-id="89d77-107">[out v] Délka vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="89d77-107">[in, out] The length of the buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89d77-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="89d77-108">Return Value</span></span>  
 <span data-ttu-id="89d77-109">Tato metoda vrací standardní kódy chyb modelu COM, jak jsou definovány v souboru WinError.h kromě následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="89d77-109">This method returns standard COM error codes, as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="89d77-110">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="89d77-110">Return code</span></span>|<span data-ttu-id="89d77-111">Popis</span><span class="sxs-lookup"><span data-stu-id="89d77-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="89d77-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="89d77-112">S_OK</span></span>|<span data-ttu-id="89d77-113">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="89d77-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="89d77-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="89d77-114">E_INVALIDARG</span></span>|`wzDir` <span data-ttu-id="89d77-115">nebo `pdwSize` má hodnotu null nebo verze řetězce je nesprávný.</span><span class="sxs-lookup"><span data-stu-id="89d77-115">or `pdwSize` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89d77-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="89d77-116">Remarks</span></span>  
 <span data-ttu-id="89d77-117">Při úspěšném dokončení `pdwSize` argument je nastaven na délku řetězce cesty.</span><span class="sxs-lookup"><span data-stu-id="89d77-117">On successful completion, the `pdwSize` argument is set to the length of the path string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89d77-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="89d77-118">Requirements</span></span>  
 <span data-ttu-id="89d77-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89d77-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89d77-120">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="89d77-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="89d77-121">**Knihovna:** Soubor Fusion.dll a knihovny Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="89d77-121">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="89d77-122">Ujistěte se, že můžete cílit na správnou verzi rozhraní .NET Framework pomocí soubor Fusion.dll namísto knihovny Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="89d77-122">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 **<span data-ttu-id="89d77-123">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="89d77-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="89d77-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89d77-124">See also</span></span>

- [<span data-ttu-id="89d77-125">CreateHistoryReader – funkce</span><span class="sxs-lookup"><span data-stu-id="89d77-125">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)
- [<span data-ttu-id="89d77-126">NukeDownloadedCache – funkce</span><span class="sxs-lookup"><span data-stu-id="89d77-126">NukeDownloadedCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)
- [<span data-ttu-id="89d77-127">Fúze globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="89d77-127">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
