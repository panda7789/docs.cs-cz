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
ms.openlocfilehash: 38c942b9a94c83f5a3316cf3ae3ccbbad2b0ec69
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444314"
---
# <a name="loadstringrcex-function"></a><span data-ttu-id="82f72-102">LoadStringRCEx – funkce</span><span class="sxs-lookup"><span data-stu-id="82f72-102">LoadStringRCEx Function</span></span>
<span data-ttu-id="82f72-103">Přeloží hodnotou HRESULT odpovídající chybové zprávy pro zadanou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="82f72-103">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="82f72-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="82f72-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82f72-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82f72-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="82f72-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="82f72-106">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="82f72-107">[v] Identifikátor jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="82f72-107">[in] A culture identifier.</span></span> <span data-ttu-id="82f72-108">Předat hodnotu -1 pro `lcid` používat výchozí jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="82f72-108">Pass -1 for `lcid` to use the default culture.</span></span>  
  
 `iResourceID`  
 <span data-ttu-id="82f72-109">[v] HRESULT.</span><span class="sxs-lookup"><span data-stu-id="82f72-109">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="82f72-110">[out] Vyrovnávací paměti, který obsahuje chybovou zprávu po úspěšném dokončení.</span><span class="sxs-lookup"><span data-stu-id="82f72-110">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="82f72-111">[v] Velikost vyrovnávací paměti chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="82f72-111">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="82f72-112">[v] Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="82f72-112">[in] Ignored.</span></span>  
  
 `pcwchUsed`  
 <span data-ttu-id="82f72-113">[out] Ukazatel na délku chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="82f72-113">[out] A pointer to the length of the error message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82f72-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="82f72-114">Return Value</span></span>  
 <span data-ttu-id="82f72-115">Tato metoda vrátí standardní kódy chyb COM, jak jsou definovány v WinError.h, kromě následující hodnoty.</span><span class="sxs-lookup"><span data-stu-id="82f72-115">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="82f72-116">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="82f72-116">Return code</span></span>|<span data-ttu-id="82f72-117">Popis</span><span class="sxs-lookup"><span data-stu-id="82f72-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="82f72-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="82f72-118">S_OK</span></span>|<span data-ttu-id="82f72-119">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="82f72-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="82f72-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="82f72-120">E_INVALIDARG</span></span>|<span data-ttu-id="82f72-121">`szBuffer` má hodnotu null, nebo `iMax` je nula (0).</span><span class="sxs-lookup"><span data-stu-id="82f72-121">`szBuffer` is null, or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82f72-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="82f72-122">Remarks</span></span>  
 <span data-ttu-id="82f72-123">Pokud metoda nedokončí úspěšně, `szBuffer` obsahuje prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="82f72-123">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82f72-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="82f72-124">Requirements</span></span>  
 <span data-ttu-id="82f72-125">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82f72-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82f72-126">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="82f72-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="82f72-127">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="82f72-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="82f72-128">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82f72-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82f72-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="82f72-129">See Also</span></span>  
 <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="82f72-130">LoadStringRC – funkce</span><span class="sxs-lookup"><span data-stu-id="82f72-130">LoadStringRC Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
 [<span data-ttu-id="82f72-131">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="82f72-131">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
