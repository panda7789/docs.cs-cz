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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a3e6230d245ad36b8d5346aa3b6f8911ef008b61
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54526844"
---
# <a name="loadstringrc-function"></a><span data-ttu-id="a0475-102">LoadStringRC – funkce</span><span class="sxs-lookup"><span data-stu-id="a0475-102">LoadStringRC Function</span></span>
<span data-ttu-id="a0475-103">Převede hodnotu HRESULT na chybovou zprávu pomocí výchozí jazykové verze aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="a0475-103">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 <span data-ttu-id="a0475-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a0475-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0475-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0475-105">Syntax</span></span>  
  
```  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0475-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a0475-106">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="a0475-107">[in] HRESULT.</span><span class="sxs-lookup"><span data-stu-id="a0475-107">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="a0475-108">[out] Vyrovnávací paměti, který obsahuje chybovou zprávu po úspěšném dokončení.</span><span class="sxs-lookup"><span data-stu-id="a0475-108">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="a0475-109">[in] Velikost vyrovnávací paměti zpráv chyby.</span><span class="sxs-lookup"><span data-stu-id="a0475-109">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="a0475-110">[in] Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="a0475-110">[in] Ignored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0475-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a0475-111">Return Value</span></span>  
 <span data-ttu-id="a0475-112">Tato metoda vrací standardní kódy chyb modelu COM (Component Object), jak je definovaný ve WinError.h, kromě následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="a0475-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="a0475-113">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="a0475-113">Return code</span></span>|<span data-ttu-id="a0475-114">Popis</span><span class="sxs-lookup"><span data-stu-id="a0475-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="a0475-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="a0475-115">S_OK</span></span>|<span data-ttu-id="a0475-116">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="a0475-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="a0475-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a0475-117">E_INVALIDARG</span></span>|<span data-ttu-id="a0475-118">`szBuffer` má hodnotu null nebo `iMax` je nula (0).</span><span class="sxs-lookup"><span data-stu-id="a0475-118">`szBuffer` is null or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0475-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a0475-119">Remarks</span></span>  
 <span data-ttu-id="a0475-120">Pokud metoda nedokončí úspěšně, `szBuffer` obsahuje prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="a0475-120">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0475-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a0475-121">Requirements</span></span>  
 <span data-ttu-id="a0475-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0475-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0475-123">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a0475-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a0475-124">**Knihovna:** MSCorEE.dll a knihovny Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="a0475-124">**Library:** MSCorEE.dll and Mscorwks.dll.</span></span> <span data-ttu-id="a0475-125">Ujistěte se, že můžete cílit na správnou verzi rozhraní .NET Framework pomocí knihovny MSCorEE.dll namísto knihovny Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="a0475-125">Use MSCorEE.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="a0475-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0475-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0475-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a0475-127">See also</span></span>
- [<span data-ttu-id="a0475-128">LoadStringRCEx – funkce</span><span class="sxs-lookup"><span data-stu-id="a0475-128">LoadStringRCEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)
- [<span data-ttu-id="a0475-129">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="a0475-129">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
