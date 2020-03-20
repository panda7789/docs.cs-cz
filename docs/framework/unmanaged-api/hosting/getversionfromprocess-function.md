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
ms.openlocfilehash: a04a0c5e6865c3664d2cb5fb341c3625e35d4d7c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178120"
---
# <a name="getversionfromprocess-function"></a><span data-ttu-id="f4288-102">GetVersionFromProcess – funkce</span><span class="sxs-lookup"><span data-stu-id="f4288-102">GetVersionFromProcess Function</span></span>
<span data-ttu-id="f4288-103">Získá číslo verze cltime společného jazyka (CLR), který je přidružen k popisovač zadaného procesu.</span><span class="sxs-lookup"><span data-stu-id="f4288-103">Gets the version number of the common language runtime (CLR) that is associated with the specified process handle.</span></span>  
  
 <span data-ttu-id="f4288-104">Tato funkce byla v rozhraní .NET Framework 4 zastaralá.</span><span class="sxs-lookup"><span data-stu-id="f4288-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4288-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4288-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4288-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f4288-106">Parameters</span></span>  
 `hProcess`  
 <span data-ttu-id="f4288-107">[v] Popisovač procesu.</span><span class="sxs-lookup"><span data-stu-id="f4288-107">[in] A handle to a process.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="f4288-108">[out] Vyrovnávací paměť, která obsahuje řetězec číslo verze po úspěšném dokončení metody.</span><span class="sxs-lookup"><span data-stu-id="f4288-108">[out] A buffer that contains the version number string upon successful completion of the method.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="f4288-109">[v] Délka vyrovnávací paměti verze.</span><span class="sxs-lookup"><span data-stu-id="f4288-109">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="f4288-110">[out] Ukazatel na délku řetězce čísla verze.</span><span class="sxs-lookup"><span data-stu-id="f4288-110">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f4288-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f4288-111">Return Value</span></span>  
 <span data-ttu-id="f4288-112">Tato metoda vrátí standardní kódy chybový model COM (COM), jak je definováno v souboru WinError.h, kromě následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="f4288-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="f4288-113">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="f4288-113">Return code</span></span>|<span data-ttu-id="f4288-114">Popis</span><span class="sxs-lookup"><span data-stu-id="f4288-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="f4288-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="f4288-115">S_OK</span></span>|<span data-ttu-id="f4288-116">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="f4288-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="f4288-117">E_invalidarg</span><span class="sxs-lookup"><span data-stu-id="f4288-117">E_INVALIDARG</span></span>|<span data-ttu-id="f4288-118">`pVersion`je null `cchBuffer` a není null nebo naopak.</span><span class="sxs-lookup"><span data-stu-id="f4288-118">`pVersion` is null and `cchBuffer` is not null, or vice versa.</span></span><br /><br /> <span data-ttu-id="f4288-119">-nebo-</span><span class="sxs-lookup"><span data-stu-id="f4288-119">-or-</span></span><br /><br /> <span data-ttu-id="f4288-120">`hProcess`není platný popisovač procesu.</span><span class="sxs-lookup"><span data-stu-id="f4288-120">`hProcess` is not a valid handle to a process.</span></span><br /><br /> <span data-ttu-id="f4288-121">-nebo-</span><span class="sxs-lookup"><span data-stu-id="f4288-121">-or-</span></span><br /><br /> <span data-ttu-id="f4288-122">CLR není načten.</span><span class="sxs-lookup"><span data-stu-id="f4288-122">The CLR is not loaded.</span></span>|  
|<span data-ttu-id="f4288-123">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="f4288-123">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="f4288-124">`cchBuffer`je null nebo menší než délka řetězce verze.</span><span class="sxs-lookup"><span data-stu-id="f4288-124">`cchBuffer` is null or less than the length of the version string.</span></span>|  
|<span data-ttu-id="f4288-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="f4288-125">E_NOTIMPL</span></span>|<span data-ttu-id="f4288-126">Tato metoda není k dispozici v operačních systémech Microsoft Windows 95, Microsoft Windows 98 nebo Microsoft Windows Millennium Edition.</span><span class="sxs-lookup"><span data-stu-id="f4288-126">This method is not available on the Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows Millennium Edition operating system.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f4288-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f4288-127">Requirements</span></span>  
 <span data-ttu-id="f4288-128">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4288-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4288-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f4288-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f4288-130">**Knihovna:** Soubor MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f4288-130">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f4288-131">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4288-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4288-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="f4288-132">See also</span></span>

- [<span data-ttu-id="f4288-133">GetRequestedRuntimeInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="f4288-133">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="f4288-134">GetRequestedRuntimeVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="f4288-134">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [<span data-ttu-id="f4288-135">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="f4288-135">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
