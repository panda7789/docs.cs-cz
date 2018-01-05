---
title: "GetVersionFromProcess – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetVersionFromProcess
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: GetVersionFromProcess
helpviewer_keywords: GetVersionFromProcess function [.NET Framework hosting]
ms.assetid: a9f7f824-64a1-408d-8607-91c7f19d21fe
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: db5054ab9b71eb93005fc0315acba82d807487ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="getversionfromprocess-function"></a><span data-ttu-id="5a23f-102">GetVersionFromProcess – funkce</span><span class="sxs-lookup"><span data-stu-id="5a23f-102">GetVersionFromProcess Function</span></span>
<span data-ttu-id="5a23f-103">Získá číslo verze common language runtime (CLR), která souvisí s popisovačem určený proces.</span><span class="sxs-lookup"><span data-stu-id="5a23f-103">Gets the version number of the common language runtime (CLR) that is associated with the specified process handle.</span></span>  
  
 <span data-ttu-id="5a23f-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5a23f-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a23f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a23f-105">Syntax</span></span>  
  
```  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *dwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a23f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5a23f-106">Parameters</span></span>  
 `hProcess`  
 <span data-ttu-id="5a23f-107">[v] Popisovač pro proces.</span><span class="sxs-lookup"><span data-stu-id="5a23f-107">[in] A handle to a process.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="5a23f-108">[out] Vyrovnávací paměť, která obsahuje řetězec číslo verze po úspěšném dokončení metody.</span><span class="sxs-lookup"><span data-stu-id="5a23f-108">[out] A buffer that contains the version number string upon successful completion of the method.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="5a23f-109">[v] Délka vyrovnávací paměti verze.</span><span class="sxs-lookup"><span data-stu-id="5a23f-109">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="5a23f-110">[out] Ukazatel na délku řetězce číslo verze.</span><span class="sxs-lookup"><span data-stu-id="5a23f-110">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5a23f-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5a23f-111">Return Value</span></span>  
 <span data-ttu-id="5a23f-112">Tato metoda vrátí standardní kódy chyb modelu COM (Component Object), jak jsou definovány v WinError.h, kromě následující hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5a23f-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="5a23f-113">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="5a23f-113">Return code</span></span>|<span data-ttu-id="5a23f-114">Popis</span><span class="sxs-lookup"><span data-stu-id="5a23f-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="5a23f-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="5a23f-115">S_OK</span></span>|<span data-ttu-id="5a23f-116">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="5a23f-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="5a23f-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="5a23f-117">E_INVALIDARG</span></span>|<span data-ttu-id="5a23f-118">`pVersion`má hodnotu null a `cchBuffer` nemá hodnotu null, nebo naopak.</span><span class="sxs-lookup"><span data-stu-id="5a23f-118">`pVersion` is null and `cchBuffer` is not null, or vice versa.</span></span><br /><br /> <span data-ttu-id="5a23f-119">-nebo-</span><span class="sxs-lookup"><span data-stu-id="5a23f-119">-or-</span></span><br /><br /> <span data-ttu-id="5a23f-120">`hProcess`není platný popisovač procesu.</span><span class="sxs-lookup"><span data-stu-id="5a23f-120">`hProcess` is not a valid handle to a process.</span></span><br /><br /> <span data-ttu-id="5a23f-121">-nebo-</span><span class="sxs-lookup"><span data-stu-id="5a23f-121">-or-</span></span><br /><br /> <span data-ttu-id="5a23f-122">Modul CLR není načtená.</span><span class="sxs-lookup"><span data-stu-id="5a23f-122">The CLR is not loaded.</span></span>|  
|<span data-ttu-id="5a23f-123">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="5a23f-123">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="5a23f-124">`cchBuffer`je null nebo být menší než délka řetězec verze.</span><span class="sxs-lookup"><span data-stu-id="5a23f-124">`cchBuffer` is null or less than the length of the version string.</span></span>|  
|<span data-ttu-id="5a23f-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="5a23f-125">E_NOTIMPL</span></span>|<span data-ttu-id="5a23f-126">Tato metoda není k dispozici v operačním systému Microsoft Windows 95, Microsoft Windows 98 nebo Microsoft Windows Millennium Edition.</span><span class="sxs-lookup"><span data-stu-id="5a23f-126">This method is not available on the Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows Millennium Edition operating system.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5a23f-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5a23f-127">Requirements</span></span>  
 <span data-ttu-id="5a23f-128">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a23f-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a23f-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5a23f-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5a23f-130">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5a23f-130">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5a23f-131">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a23f-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a23f-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a23f-132">See Also</span></span>  
 [<span data-ttu-id="5a23f-133">GetRequestedRuntimeInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="5a23f-133">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 [<span data-ttu-id="5a23f-134">GetRequestedRuntimeVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="5a23f-134">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 [<span data-ttu-id="5a23f-135">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="5a23f-135">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
