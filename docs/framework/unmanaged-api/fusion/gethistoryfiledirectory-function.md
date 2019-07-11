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
ms.openlocfilehash: 10eead2772a2bbd8abaf7b9c090a091687725972
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778650"
---
# <a name="gethistoryfiledirectory-function"></a><span data-ttu-id="1fd23-102">GetHistoryFileDirectory – funkce</span><span class="sxs-lookup"><span data-stu-id="1fd23-102">GetHistoryFileDirectory Function</span></span>
<span data-ttu-id="1fd23-103">Načte cestu adresáře historie aplikace.</span><span class="sxs-lookup"><span data-stu-id="1fd23-103">Retrieves the path of the application history directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fd23-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1fd23-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1fd23-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1fd23-105">Parameters</span></span>  
 `wzDir`  
 <span data-ttu-id="1fd23-106">[out] Vyrovnávací paměť pro cestu k adresáři aplikace historie.</span><span class="sxs-lookup"><span data-stu-id="1fd23-106">[out] A buffer to hold the path to the application history directory.</span></span>  
  
 `pdwSize`  
 <span data-ttu-id="1fd23-107">[out v] Délka vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="1fd23-107">[in, out] The length of the buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1fd23-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1fd23-108">Return Value</span></span>  
 <span data-ttu-id="1fd23-109">Tato metoda vrací standardní kódy chyb modelu COM, jak jsou definovány v souboru WinError.h kromě následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="1fd23-109">This method returns standard COM error codes, as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="1fd23-110">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="1fd23-110">Return code</span></span>|<span data-ttu-id="1fd23-111">Popis</span><span class="sxs-lookup"><span data-stu-id="1fd23-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="1fd23-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="1fd23-112">S_OK</span></span>|<span data-ttu-id="1fd23-113">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="1fd23-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="1fd23-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="1fd23-114">E_INVALIDARG</span></span>|<span data-ttu-id="1fd23-115">`wzDir` nebo `pdwSize` má hodnotu null nebo verze řetězce je nesprávný.</span><span class="sxs-lookup"><span data-stu-id="1fd23-115">`wzDir` or `pdwSize` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1fd23-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1fd23-116">Remarks</span></span>  
 <span data-ttu-id="1fd23-117">Při úspěšném dokončení `pdwSize` argument je nastaven na délku řetězce cesty.</span><span class="sxs-lookup"><span data-stu-id="1fd23-117">On successful completion, the `pdwSize` argument is set to the length of the path string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fd23-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1fd23-118">Requirements</span></span>  
 <span data-ttu-id="1fd23-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1fd23-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fd23-120">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="1fd23-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="1fd23-121">**Knihovna:** Soubor Fusion.dll a knihovny Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="1fd23-121">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="1fd23-122">Ujistěte se, že můžete cílit na správnou verzi rozhraní .NET Framework pomocí soubor Fusion.dll namísto knihovny Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="1fd23-122">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="1fd23-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fd23-123">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fd23-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1fd23-124">See also</span></span>

- [<span data-ttu-id="1fd23-125">CreateHistoryReader – funkce</span><span class="sxs-lookup"><span data-stu-id="1fd23-125">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)
- [<span data-ttu-id="1fd23-126">NukeDownloadedCache – funkce</span><span class="sxs-lookup"><span data-stu-id="1fd23-126">NukeDownloadedCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)
- [<span data-ttu-id="1fd23-127">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="1fd23-127">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
