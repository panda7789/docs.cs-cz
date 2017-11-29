---
title: "LoadStringRC – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LoadStringRC
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: LoadStringRC
helpviewer_keywords: LoadStringRC function [.NET Framework hosting]
ms.assetid: 752e49b4-987c-4c28-a118-1a0c1ed510c5
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bc93adf575af7f2803b20f24a3261a447772ffd4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="loadstringrc-function"></a><span data-ttu-id="abd10-102">LoadStringRC – funkce</span><span class="sxs-lookup"><span data-stu-id="abd10-102">LoadStringRC Function</span></span>
<span data-ttu-id="abd10-103">Změní hodnotu HRESULT na chybovou zprávu pomocí výchozí jazykové verze aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="abd10-103">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 <span data-ttu-id="abd10-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="abd10-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abd10-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="abd10-105">Syntax</span></span>  
  
```  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="abd10-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="abd10-106">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="abd10-107">[v] HRESULT.</span><span class="sxs-lookup"><span data-stu-id="abd10-107">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="abd10-108">[out] Vyrovnávací paměti, který obsahuje chybovou zprávu po úspěšném dokončení.</span><span class="sxs-lookup"><span data-stu-id="abd10-108">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="abd10-109">[v] Velikost vyrovnávací paměti chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="abd10-109">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="abd10-110">[v] Ignorovat.</span><span class="sxs-lookup"><span data-stu-id="abd10-110">[in] Ignored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="abd10-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="abd10-111">Return Value</span></span>  
 <span data-ttu-id="abd10-112">Tato metoda vrátí standardní kódy chyb modelu COM (Component Object), jak jsou definovány v WinError.h, kromě následující hodnoty.</span><span class="sxs-lookup"><span data-stu-id="abd10-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="abd10-113">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="abd10-113">Return code</span></span>|<span data-ttu-id="abd10-114">Popis</span><span class="sxs-lookup"><span data-stu-id="abd10-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="abd10-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="abd10-115">S_OK</span></span>|<span data-ttu-id="abd10-116">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="abd10-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="abd10-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="abd10-117">E_INVALIDARG</span></span>|<span data-ttu-id="abd10-118">`szBuffer`má hodnotu null nebo `iMax` je nula (0).</span><span class="sxs-lookup"><span data-stu-id="abd10-118">`szBuffer` is null or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="abd10-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="abd10-119">Remarks</span></span>  
 <span data-ttu-id="abd10-120">Pokud metoda nedokončí úspěšně, `szBuffer` obsahuje prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="abd10-120">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abd10-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="abd10-121">Requirements</span></span>  
 <span data-ttu-id="abd10-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abd10-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abd10-123">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="abd10-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="abd10-124">**Knihovna:** MSCorEE.dll a Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="abd10-124">**Library:** MSCorEE.dll and Mscorwks.dll.</span></span> <span data-ttu-id="abd10-125">Pomocí MSCorEE.dll místo Mscorwks.dll zajistit, na které cílí správnou verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="abd10-125">Use MSCorEE.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="abd10-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abd10-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abd10-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="abd10-127">See Also</span></span>  
 [<span data-ttu-id="abd10-128">Loadstringrcex – funkce</span><span class="sxs-lookup"><span data-stu-id="abd10-128">LoadStringRCEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
 [<span data-ttu-id="abd10-129">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="abd10-129">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
