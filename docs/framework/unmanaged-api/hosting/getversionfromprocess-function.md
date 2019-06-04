---
title: GetVersionFromProcess – funkce
ms.date: 03/30/2017
api_name:
- GetVersionFromProcess
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetVersionFromProcess
helpviewer_keywords:
- GetVersionFromProcess function [.NET Framework hosting]
ms.assetid: a9f7f824-64a1-408d-8607-91c7f19d21fe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3055ac73f15329015f532f42c1f922eab38828cb
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490303"
---
# <a name="getversionfromprocess-function"></a><span data-ttu-id="5bf11-102">GetVersionFromProcess – funkce</span><span class="sxs-lookup"><span data-stu-id="5bf11-102">GetVersionFromProcess Function</span></span>
<span data-ttu-id="5bf11-103">Získá číslo verze common language runtime (CLR), který je spojen s obslužnou rutinou určeného procesu.</span><span class="sxs-lookup"><span data-stu-id="5bf11-103">Gets the version number of the common language runtime (CLR) that is associated with the specified process handle.</span></span>  
  
 <span data-ttu-id="5bf11-104">Tato funkce se již nepoužívá v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="5bf11-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bf11-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5bf11-105">Syntax</span></span>  
  
```  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bf11-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5bf11-106">Parameters</span></span>  
 `hProcess`  
 <span data-ttu-id="5bf11-107">[in] Popisovač procesu.</span><span class="sxs-lookup"><span data-stu-id="5bf11-107">[in] A handle to a process.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="5bf11-108">[out] Vyrovnávací paměť, která obsahuje řetězec, číslo verze po úspěšném dokončení metody.</span><span class="sxs-lookup"><span data-stu-id="5bf11-108">[out] A buffer that contains the version number string upon successful completion of the method.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="5bf11-109">[in] Délka vyrovnávací paměti verze.</span><span class="sxs-lookup"><span data-stu-id="5bf11-109">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="5bf11-110">[out] Ukazatel na délku řetězce číslo verze.</span><span class="sxs-lookup"><span data-stu-id="5bf11-110">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5bf11-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5bf11-111">Return Value</span></span>  
 <span data-ttu-id="5bf11-112">Tato metoda vrací standardní kódy chyb modelu COM (Component Object), jak je definovaný ve WinError.h, kromě následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="5bf11-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="5bf11-113">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="5bf11-113">Return code</span></span>|<span data-ttu-id="5bf11-114">Popis</span><span class="sxs-lookup"><span data-stu-id="5bf11-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="5bf11-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="5bf11-115">S_OK</span></span>|<span data-ttu-id="5bf11-116">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="5bf11-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="5bf11-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="5bf11-117">E_INVALIDARG</span></span>|<span data-ttu-id="5bf11-118">`pVersion` má hodnotu null a `cchBuffer` nemá hodnotu null, nebo naopak.</span><span class="sxs-lookup"><span data-stu-id="5bf11-118">`pVersion` is null and `cchBuffer` is not null, or vice versa.</span></span><br /><br /> <span data-ttu-id="5bf11-119">-nebo-</span><span class="sxs-lookup"><span data-stu-id="5bf11-119">-or-</span></span><br /><br /> <span data-ttu-id="5bf11-120">`hProcess` není platný popisovač procesu.</span><span class="sxs-lookup"><span data-stu-id="5bf11-120">`hProcess` is not a valid handle to a process.</span></span><br /><br /> <span data-ttu-id="5bf11-121">-nebo-</span><span class="sxs-lookup"><span data-stu-id="5bf11-121">-or-</span></span><br /><br /> <span data-ttu-id="5bf11-122">Není načten modul CLR.</span><span class="sxs-lookup"><span data-stu-id="5bf11-122">The CLR is not loaded.</span></span>|  
|<span data-ttu-id="5bf11-123">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="5bf11-123">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="5bf11-124">`cchBuffer` je null nebo je menší než délka řetězce verze.</span><span class="sxs-lookup"><span data-stu-id="5bf11-124">`cchBuffer` is null or less than the length of the version string.</span></span>|  
|<span data-ttu-id="5bf11-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="5bf11-125">E_NOTIMPL</span></span>|<span data-ttu-id="5bf11-126">Tato metoda není k dispozici v operačním systému Microsoft Windows 95, Microsoft Windows 98 nebo Microsoft Windows Millennium Edition.</span><span class="sxs-lookup"><span data-stu-id="5bf11-126">This method is not available on the Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows Millennium Edition operating system.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5bf11-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5bf11-127">Requirements</span></span>  
 <span data-ttu-id="5bf11-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bf11-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bf11-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5bf11-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5bf11-130">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5bf11-130">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5bf11-131">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bf11-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bf11-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5bf11-132">See also</span></span>

- [<span data-ttu-id="5bf11-133">GetRequestedRuntimeInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="5bf11-133">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="5bf11-134">GetRequestedRuntimeVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="5bf11-134">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [<span data-ttu-id="5bf11-135">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="5bf11-135">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
