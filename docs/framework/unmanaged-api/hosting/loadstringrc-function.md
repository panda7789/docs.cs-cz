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
ms.openlocfilehash: 66d4c14234c7929af443922f86098b46a4aa6eb7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122021"
---
# <a name="loadstringrc-function"></a><span data-ttu-id="89dda-102">LoadStringRC – funkce</span><span class="sxs-lookup"><span data-stu-id="89dda-102">LoadStringRC Function</span></span>
<span data-ttu-id="89dda-103">Přeloží hodnotu HRESULT na chybovou zprávu pomocí výchozí jazykové verze aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="89dda-103">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 <span data-ttu-id="89dda-104">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="89dda-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89dda-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89dda-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89dda-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="89dda-106">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="89dda-107">pro HRESULT.</span><span class="sxs-lookup"><span data-stu-id="89dda-107">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="89dda-108">mimo Vyrovnávací paměť, která obsahuje chybovou zprávu po úspěšném dokončení.</span><span class="sxs-lookup"><span data-stu-id="89dda-108">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="89dda-109">pro Velikost vyrovnávací paměti chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="89dda-109">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="89dda-110">pro Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="89dda-110">[in] Ignored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89dda-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="89dda-111">Return Value</span></span>  
 <span data-ttu-id="89dda-112">Tato metoda vrátí standardní kódy chyb modelu COM (Component Object Model), jak je definováno v WinError. h, kromě následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="89dda-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="89dda-113">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="89dda-113">Return code</span></span>|<span data-ttu-id="89dda-114">Popis</span><span class="sxs-lookup"><span data-stu-id="89dda-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="89dda-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="89dda-115">S_OK</span></span>|<span data-ttu-id="89dda-116">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="89dda-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="89dda-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="89dda-117">E_INVALIDARG</span></span>|<span data-ttu-id="89dda-118">`szBuffer` má hodnotu null nebo je `iMax` nula (0).</span><span class="sxs-lookup"><span data-stu-id="89dda-118">`szBuffer` is null or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89dda-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="89dda-119">Remarks</span></span>  
 <span data-ttu-id="89dda-120">Pokud metoda není úspěšně dokončena, `szBuffer` obsahuje prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="89dda-120">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89dda-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="89dda-121">Requirements</span></span>  
 <span data-ttu-id="89dda-122">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89dda-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89dda-123">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="89dda-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="89dda-124">**Knihovna:** MSCorEE. dll a knihovny Mscorwks. dll.</span><span class="sxs-lookup"><span data-stu-id="89dda-124">**Library:** MSCorEE.dll and Mscorwks.dll.</span></span> <span data-ttu-id="89dda-125">Použijte knihovnu MSCorEE. dll namísto knihovny Mscorwks. dll, abyste se ujistili, že cílíte na správnou verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="89dda-125">Use MSCorEE.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="89dda-126">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89dda-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89dda-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89dda-127">See also</span></span>

- [<span data-ttu-id="89dda-128">LoadStringRCEx – funkce</span><span class="sxs-lookup"><span data-stu-id="89dda-128">LoadStringRCEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)
- [<span data-ttu-id="89dda-129">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="89dda-129">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
