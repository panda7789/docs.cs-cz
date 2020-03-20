---
title: LoadStringRC – funkce
ms.date: 03/30/2017
api_name:
- LoadStringRC
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRC
helpviewer_keywords:
- LoadStringRC function [.NET Framework hosting]
ms.assetid: 752e49b4-987c-4c28-a118-1a0c1ed510c5
topic_type:
- apiref
ms.openlocfilehash: 56ae7b7cf3b577bfe41ebd0bdd98e0da68047b44
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176237"
---
# <a name="loadstringrc-function"></a><span data-ttu-id="3993f-102">LoadStringRC – funkce</span><span class="sxs-lookup"><span data-stu-id="3993f-102">LoadStringRC Function</span></span>
<span data-ttu-id="3993f-103">Převede hodnotu HRESULT na chybovou zprávu pomocí výchozí jazykové verze aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="3993f-103">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 <span data-ttu-id="3993f-104">Tato funkce byla v rozhraní .NET Framework 4 zastaralá.</span><span class="sxs-lookup"><span data-stu-id="3993f-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3993f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3993f-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,
    [out] LPWSTR  szBuffer,
    [in]  int     iMax,
    [in]  int     bQuiet  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3993f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3993f-106">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="3993f-107">[v] An HRESULT.</span><span class="sxs-lookup"><span data-stu-id="3993f-107">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="3993f-108">[out] Vyrovnávací paměť, která obsahuje chybovou zprávu po úspěšném dokončení.</span><span class="sxs-lookup"><span data-stu-id="3993f-108">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="3993f-109">[v] Velikost vyrovnávací paměti chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="3993f-109">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="3993f-110">[v] Ignorovány.</span><span class="sxs-lookup"><span data-stu-id="3993f-110">[in] Ignored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3993f-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3993f-111">Return Value</span></span>  
 <span data-ttu-id="3993f-112">Tato metoda vrátí standardní kódy chybový model COM (COM), jak je definováno v souboru WinError.h, kromě následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="3993f-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="3993f-113">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="3993f-113">Return code</span></span>|<span data-ttu-id="3993f-114">Popis</span><span class="sxs-lookup"><span data-stu-id="3993f-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="3993f-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="3993f-115">S_OK</span></span>|<span data-ttu-id="3993f-116">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="3993f-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="3993f-117">E_invalidarg</span><span class="sxs-lookup"><span data-stu-id="3993f-117">E_INVALIDARG</span></span>|<span data-ttu-id="3993f-118">`szBuffer`je null `iMax` nebo je nula (0).</span><span class="sxs-lookup"><span data-stu-id="3993f-118">`szBuffer` is null or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3993f-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3993f-119">Remarks</span></span>  
 <span data-ttu-id="3993f-120">Pokud metoda není úspěšně dokončena, `szBuffer` obsahuje prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="3993f-120">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3993f-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3993f-121">Requirements</span></span>  
 <span data-ttu-id="3993f-122">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3993f-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3993f-123">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3993f-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3993f-124">**Knihovna:** MSCorEE.dll a Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="3993f-124">**Library:** MSCorEE.dll and Mscorwks.dll.</span></span> <span data-ttu-id="3993f-125">Místo souboru Mscorwks.dll použijte soubor MSCorEE.dll a ujistěte se, že cílíte na správnou verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3993f-125">Use MSCorEE.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="3993f-126">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3993f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3993f-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="3993f-127">See also</span></span>

- [<span data-ttu-id="3993f-128">LoadStringRCEx – funkce</span><span class="sxs-lookup"><span data-stu-id="3993f-128">LoadStringRCEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)
- [<span data-ttu-id="3993f-129">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="3993f-129">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
