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
ms.openlocfilehash: 1aabfad14ee2eb35916bbf115631602276cd1fc3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109897"
---
# <a name="gethistoryfiledirectory-function"></a><span data-ttu-id="14c6f-102">GetHistoryFileDirectory – funkce</span><span class="sxs-lookup"><span data-stu-id="14c6f-102">GetHistoryFileDirectory Function</span></span>
<span data-ttu-id="14c6f-103">Načte cestu k adresáři historie aplikace.</span><span class="sxs-lookup"><span data-stu-id="14c6f-103">Retrieves the path of the application history directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14c6f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14c6f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14c6f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="14c6f-105">Parameters</span></span>  
 `wzDir`  
 <span data-ttu-id="14c6f-106">mimo Vyrovnávací paměť pro uložení cesty k adresáři historie aplikace</span><span class="sxs-lookup"><span data-stu-id="14c6f-106">[out] A buffer to hold the path to the application history directory.</span></span>  
  
 `pdwSize`  
 <span data-ttu-id="14c6f-107">[in, out] Délka vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="14c6f-107">[in, out] The length of the buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="14c6f-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="14c6f-108">Return Value</span></span>  
 <span data-ttu-id="14c6f-109">Tato metoda vrací standardní chybové kódy modelu COM, jak jsou definovány v souboru WinError. h, kromě následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="14c6f-109">This method returns standard COM error codes, as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="14c6f-110">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="14c6f-110">Return code</span></span>|<span data-ttu-id="14c6f-111">Popis</span><span class="sxs-lookup"><span data-stu-id="14c6f-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="14c6f-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="14c6f-112">S_OK</span></span>|<span data-ttu-id="14c6f-113">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="14c6f-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="14c6f-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="14c6f-114">E_INVALIDARG</span></span>|<span data-ttu-id="14c6f-115">`wzDir` nebo `pdwSize` je null nebo je řetězec verze nesprávný.</span><span class="sxs-lookup"><span data-stu-id="14c6f-115">`wzDir` or `pdwSize` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14c6f-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="14c6f-116">Remarks</span></span>  
 <span data-ttu-id="14c6f-117">Po úspěšném dokončení se argument `pdwSize` nastaví na délku řetězce cesty.</span><span class="sxs-lookup"><span data-stu-id="14c6f-117">On successful completion, the `pdwSize` argument is set to the length of the path string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14c6f-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="14c6f-118">Requirements</span></span>  
 <span data-ttu-id="14c6f-119">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14c6f-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14c6f-120">**Hlavička:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="14c6f-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="14c6f-121">**Knihovna:** Fusion. dll a knihovny Mscorwks. dll.</span><span class="sxs-lookup"><span data-stu-id="14c6f-121">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="14c6f-122">Použijte knihovnu Fusion. dll namísto knihovny Mscorwks. dll, abyste se ujistili, že cílíte na správnou verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="14c6f-122">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="14c6f-123">**Verze .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14c6f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14c6f-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14c6f-124">See also</span></span>

- [<span data-ttu-id="14c6f-125">CreateHistoryReader – funkce</span><span class="sxs-lookup"><span data-stu-id="14c6f-125">CreateHistoryReader Function</span></span>](createhistoryreader-function.md)
- [<span data-ttu-id="14c6f-126">NukeDownloadedCache – funkce</span><span class="sxs-lookup"><span data-stu-id="14c6f-126">NukeDownloadedCache Function</span></span>](nukedownloadedcache-function.md)
- [<span data-ttu-id="14c6f-127">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="14c6f-127">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
