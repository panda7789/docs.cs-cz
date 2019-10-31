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
ms.openlocfilehash: 76c033b11f3212241827d74f4fe18ee881f20b64
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127040"
---
# <a name="getversionfromprocess-function"></a><span data-ttu-id="f8bc1-102">GetVersionFromProcess – funkce</span><span class="sxs-lookup"><span data-stu-id="f8bc1-102">GetVersionFromProcess Function</span></span>
<span data-ttu-id="f8bc1-103">Získá číslo verze modulu CLR (Common Language Runtime), který je spojen se zadaným popisovačem procesu.</span><span class="sxs-lookup"><span data-stu-id="f8bc1-103">Gets the version number of the common language runtime (CLR) that is associated with the specified process handle.</span></span>  
  
 <span data-ttu-id="f8bc1-104">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="f8bc1-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8bc1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8bc1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8bc1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8bc1-106">Parameters</span></span>  
 `hProcess`  
 <span data-ttu-id="f8bc1-107">pro Popisovač procesu.</span><span class="sxs-lookup"><span data-stu-id="f8bc1-107">[in] A handle to a process.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="f8bc1-108">mimo Vyrovnávací paměť, která obsahuje řetězec čísla verze po úspěšném dokončení metody.</span><span class="sxs-lookup"><span data-stu-id="f8bc1-108">[out] A buffer that contains the version number string upon successful completion of the method.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="f8bc1-109">pro Délka vyrovnávací paměti verze.</span><span class="sxs-lookup"><span data-stu-id="f8bc1-109">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="f8bc1-110">mimo Ukazatel na délku řetězce čísla verze.</span><span class="sxs-lookup"><span data-stu-id="f8bc1-110">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f8bc1-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f8bc1-111">Return Value</span></span>  
 <span data-ttu-id="f8bc1-112">Tato metoda vrátí standardní kódy chyb modelu COM (Component Object Model), jak je definováno v WinError. h, kromě následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="f8bc1-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="f8bc1-113">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="f8bc1-113">Return code</span></span>|<span data-ttu-id="f8bc1-114">Popis</span><span class="sxs-lookup"><span data-stu-id="f8bc1-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="f8bc1-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="f8bc1-115">S_OK</span></span>|<span data-ttu-id="f8bc1-116">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="f8bc1-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="f8bc1-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f8bc1-117">E_INVALIDARG</span></span>|<span data-ttu-id="f8bc1-118">`pVersion` je null a `cchBuffer` není null, nebo naopak.</span><span class="sxs-lookup"><span data-stu-id="f8bc1-118">`pVersion` is null and `cchBuffer` is not null, or vice versa.</span></span><br /><br /> <span data-ttu-id="f8bc1-119">-nebo-</span><span class="sxs-lookup"><span data-stu-id="f8bc1-119">-or-</span></span><br /><br /> <span data-ttu-id="f8bc1-120">`hProcess` není platným popisovačem procesu.</span><span class="sxs-lookup"><span data-stu-id="f8bc1-120">`hProcess` is not a valid handle to a process.</span></span><br /><br /> <span data-ttu-id="f8bc1-121">-nebo-</span><span class="sxs-lookup"><span data-stu-id="f8bc1-121">-or-</span></span><br /><br /> <span data-ttu-id="f8bc1-122">Modul CLR není zaveden.</span><span class="sxs-lookup"><span data-stu-id="f8bc1-122">The CLR is not loaded.</span></span>|  
|<span data-ttu-id="f8bc1-123">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="f8bc1-123">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="f8bc1-124">`cchBuffer` je null nebo menší než délka řetězce verze.</span><span class="sxs-lookup"><span data-stu-id="f8bc1-124">`cchBuffer` is null or less than the length of the version string.</span></span>|  
|<span data-ttu-id="f8bc1-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="f8bc1-125">E_NOTIMPL</span></span>|<span data-ttu-id="f8bc1-126">Tato metoda není k dispozici v operačním systému Microsoft Windows 95, Microsoft Windows 98 nebo Microsoft Windows Millennium Edition.</span><span class="sxs-lookup"><span data-stu-id="f8bc1-126">This method is not available on the Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows Millennium Edition operating system.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f8bc1-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f8bc1-127">Requirements</span></span>  
 <span data-ttu-id="f8bc1-128">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8bc1-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8bc1-129">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f8bc1-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f8bc1-130">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f8bc1-130">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f8bc1-131">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8bc1-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8bc1-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8bc1-132">See also</span></span>

- [<span data-ttu-id="f8bc1-133">GetRequestedRuntimeInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="f8bc1-133">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="f8bc1-134">GetRequestedRuntimeVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="f8bc1-134">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [<span data-ttu-id="f8bc1-135">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="f8bc1-135">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
