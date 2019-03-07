---
title: LoadStringRCEx – funkce
ms.date: 03/30/2017
api_name:
- LoadStringRCEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRCEx
helpviewer_keywords:
- LoadStringRCEx function [.NET Framework hosting]
ms.assetid: bc789636-ca14-4f07-8f77-9305874d7495
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c3185bdc0776d6536458ce03c348ed77b8ba0b9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499092"
---
# <a name="loadstringrcex-function"></a><span data-ttu-id="e4f10-102">LoadStringRCEx – funkce</span><span class="sxs-lookup"><span data-stu-id="e4f10-102">LoadStringRCEx Function</span></span>
<span data-ttu-id="e4f10-103">Převede hodnotu HRESULT na příslušnou chybovou zprávu pro zadanou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="e4f10-103">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="e4f10-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e4f10-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4f10-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4f10-105">Syntax</span></span>  
  
```  
HRESULT LoadStringRCEx (  
    [in]  LCID    lcid,   
    [in]  UINT    iResouceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet,   
    [out] int    *pcwchUsed  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4f10-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e4f10-106">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="e4f10-107">[in] Identifikátor jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="e4f10-107">[in] A culture identifier.</span></span> <span data-ttu-id="e4f10-108">Předejte hodnotu -1 `lcid` používat výchozí jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="e4f10-108">Pass -1 for `lcid` to use the default culture.</span></span>  
  
 `iResourceID`  
 <span data-ttu-id="e4f10-109">[in] HRESULT.</span><span class="sxs-lookup"><span data-stu-id="e4f10-109">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="e4f10-110">[out] Vyrovnávací paměti, který obsahuje chybovou zprávu po úspěšném dokončení.</span><span class="sxs-lookup"><span data-stu-id="e4f10-110">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="e4f10-111">[in] Velikost vyrovnávací paměti zpráv chyby.</span><span class="sxs-lookup"><span data-stu-id="e4f10-111">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="e4f10-112">[in] Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="e4f10-112">[in] Ignored.</span></span>  
  
 `pcwchUsed`  
 <span data-ttu-id="e4f10-113">[out] Ukazatel na délku chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="e4f10-113">[out] A pointer to the length of the error message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e4f10-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e4f10-114">Return Value</span></span>  
 <span data-ttu-id="e4f10-115">Tato metoda vrací standardní kódy chyb modelu COM, jak je definovaný ve WinError.h, kromě následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="e4f10-115">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="e4f10-116">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="e4f10-116">Return code</span></span>|<span data-ttu-id="e4f10-117">Popis</span><span class="sxs-lookup"><span data-stu-id="e4f10-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="e4f10-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="e4f10-118">S_OK</span></span>|<span data-ttu-id="e4f10-119">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="e4f10-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="e4f10-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e4f10-120">E_INVALIDARG</span></span>|<span data-ttu-id="e4f10-121">`szBuffer` má hodnotu null, nebo `iMax` je nula (0).</span><span class="sxs-lookup"><span data-stu-id="e4f10-121">`szBuffer` is null, or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4f10-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e4f10-122">Remarks</span></span>  
 <span data-ttu-id="e4f10-123">Pokud metoda nedokončí úspěšně, `szBuffer` obsahuje prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="e4f10-123">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4f10-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e4f10-124">Requirements</span></span>  
 <span data-ttu-id="e4f10-125">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4f10-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4f10-126">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e4f10-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e4f10-127">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e4f10-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e4f10-128">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4f10-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4f10-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4f10-129">See also</span></span>
- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e4f10-130">LoadStringRC – funkce</span><span class="sxs-lookup"><span data-stu-id="e4f10-130">LoadStringRC Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)
- [<span data-ttu-id="e4f10-131">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="e4f10-131">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
