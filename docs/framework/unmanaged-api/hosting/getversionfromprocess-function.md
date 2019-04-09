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
ms.openlocfilehash: 452104939acf5de7bb151cba00d65fb6631c98d5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124082"
---
# <a name="getversionfromprocess-function"></a><span data-ttu-id="6fd81-102">GetVersionFromProcess – funkce</span><span class="sxs-lookup"><span data-stu-id="6fd81-102">GetVersionFromProcess Function</span></span>
<span data-ttu-id="6fd81-103">Získá číslo verze common language runtime (CLR), který je spojen s obslužnou rutinou určeného procesu.</span><span class="sxs-lookup"><span data-stu-id="6fd81-103">Gets the version number of the common language runtime (CLR) that is associated with the specified process handle.</span></span>  
  
 <span data-ttu-id="6fd81-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6fd81-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fd81-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6fd81-105">Syntax</span></span>  
  
```  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6fd81-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6fd81-106">Parameters</span></span>  
 `hProcess`  
 <span data-ttu-id="6fd81-107">[in] Popisovač procesu.</span><span class="sxs-lookup"><span data-stu-id="6fd81-107">[in] A handle to a process.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="6fd81-108">[out] Vyrovnávací paměť, která obsahuje řetězec, číslo verze po úspěšném dokončení metody.</span><span class="sxs-lookup"><span data-stu-id="6fd81-108">[out] A buffer that contains the version number string upon successful completion of the method.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="6fd81-109">[in] Délka vyrovnávací paměti verze.</span><span class="sxs-lookup"><span data-stu-id="6fd81-109">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="6fd81-110">[out] Ukazatel na délku řetězce číslo verze.</span><span class="sxs-lookup"><span data-stu-id="6fd81-110">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6fd81-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6fd81-111">Return Value</span></span>  
 <span data-ttu-id="6fd81-112">Tato metoda vrací standardní kódy chyb modelu COM (Component Object), jak je definovaný ve WinError.h, kromě následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="6fd81-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="6fd81-113">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="6fd81-113">Return code</span></span>|<span data-ttu-id="6fd81-114">Popis</span><span class="sxs-lookup"><span data-stu-id="6fd81-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="6fd81-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="6fd81-115">S_OK</span></span>|<span data-ttu-id="6fd81-116">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="6fd81-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="6fd81-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="6fd81-117">E_INVALIDARG</span></span>|`pVersion` <span data-ttu-id="6fd81-118">má hodnotu null a `cchBuffer` nemá hodnotu null, nebo naopak.</span><span class="sxs-lookup"><span data-stu-id="6fd81-118">is null and `cchBuffer` is not null, or vice versa.</span></span><br /><br /> <span data-ttu-id="6fd81-119">-nebo-</span><span class="sxs-lookup"><span data-stu-id="6fd81-119">-or-</span></span><br /><br /> `hProcess` <span data-ttu-id="6fd81-120">není platný popisovač procesu.</span><span class="sxs-lookup"><span data-stu-id="6fd81-120">is not a valid handle to a process.</span></span><br /><br /> <span data-ttu-id="6fd81-121">-nebo-</span><span class="sxs-lookup"><span data-stu-id="6fd81-121">-or-</span></span><br /><br /> <span data-ttu-id="6fd81-122">Není načten modul CLR.</span><span class="sxs-lookup"><span data-stu-id="6fd81-122">The CLR is not loaded.</span></span>|  
|<span data-ttu-id="6fd81-123">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="6fd81-123">ERROR_INSUFFICIENT_BUFFER</span></span>|`cchBuffer` <span data-ttu-id="6fd81-124">je null nebo je menší než délka řetězce verze.</span><span class="sxs-lookup"><span data-stu-id="6fd81-124">is null or less than the length of the version string.</span></span>|  
|<span data-ttu-id="6fd81-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="6fd81-125">E_NOTIMPL</span></span>|<span data-ttu-id="6fd81-126">Tato metoda není k dispozici v operačním systému Microsoft Windows 95, Microsoft Windows 98 nebo Microsoft Windows Millennium Edition.</span><span class="sxs-lookup"><span data-stu-id="6fd81-126">This method is not available on the Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows Millennium Edition operating system.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6fd81-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6fd81-127">Requirements</span></span>  
 <span data-ttu-id="6fd81-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fd81-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fd81-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6fd81-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6fd81-130">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6fd81-130">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="6fd81-131">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="6fd81-131">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6fd81-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6fd81-132">See also</span></span>

- [<span data-ttu-id="6fd81-133">GetRequestedRuntimeInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="6fd81-133">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="6fd81-134">GetRequestedRuntimeVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="6fd81-134">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [<span data-ttu-id="6fd81-135">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="6fd81-135">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
