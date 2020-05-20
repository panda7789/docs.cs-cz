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
ms.openlocfilehash: fbaf45da0902ded8a2f7bf0d470aaed3b5f531aa
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617123"
---
# <a name="getversionfromprocess-function"></a><span data-ttu-id="83f03-102">GetVersionFromProcess – funkce</span><span class="sxs-lookup"><span data-stu-id="83f03-102">GetVersionFromProcess Function</span></span>
<span data-ttu-id="83f03-103">Získá číslo verze modulu CLR (Common Language Runtime), který je spojen se zadaným popisovačem procesu.</span><span class="sxs-lookup"><span data-stu-id="83f03-103">Gets the version number of the common language runtime (CLR) that is associated with the specified process handle.</span></span>  
  
 <span data-ttu-id="83f03-104">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="83f03-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83f03-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83f03-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83f03-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="83f03-106">Parameters</span></span>  
 `hProcess`  
 <span data-ttu-id="83f03-107">pro Popisovač procesu.</span><span class="sxs-lookup"><span data-stu-id="83f03-107">[in] A handle to a process.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="83f03-108">mimo Vyrovnávací paměť, která obsahuje řetězec čísla verze po úspěšném dokončení metody.</span><span class="sxs-lookup"><span data-stu-id="83f03-108">[out] A buffer that contains the version number string upon successful completion of the method.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="83f03-109">pro Délka vyrovnávací paměti verze.</span><span class="sxs-lookup"><span data-stu-id="83f03-109">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="83f03-110">mimo Ukazatel na délku řetězce čísla verze.</span><span class="sxs-lookup"><span data-stu-id="83f03-110">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83f03-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="83f03-111">Return Value</span></span>  
 <span data-ttu-id="83f03-112">Tato metoda vrátí standardní kódy chyb modelu COM (Component Object Model), jak je definováno v WinError. h, kromě následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="83f03-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="83f03-113">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="83f03-113">Return code</span></span>|<span data-ttu-id="83f03-114">Popis</span><span class="sxs-lookup"><span data-stu-id="83f03-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="83f03-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="83f03-115">S_OK</span></span>|<span data-ttu-id="83f03-116">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="83f03-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="83f03-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="83f03-117">E_INVALIDARG</span></span>|<span data-ttu-id="83f03-118">`pVersion`má hodnotu null a `cchBuffer` není null nebo naopak.</span><span class="sxs-lookup"><span data-stu-id="83f03-118">`pVersion` is null and `cchBuffer` is not null, or vice versa.</span></span><br /><br /> <span data-ttu-id="83f03-119">-nebo-</span><span class="sxs-lookup"><span data-stu-id="83f03-119">-or-</span></span><br /><br /> <span data-ttu-id="83f03-120">`hProcess`není platným popisovačem procesu.</span><span class="sxs-lookup"><span data-stu-id="83f03-120">`hProcess` is not a valid handle to a process.</span></span><br /><br /> <span data-ttu-id="83f03-121">-nebo-</span><span class="sxs-lookup"><span data-stu-id="83f03-121">-or-</span></span><br /><br /> <span data-ttu-id="83f03-122">Modul CLR není zaveden.</span><span class="sxs-lookup"><span data-stu-id="83f03-122">The CLR is not loaded.</span></span>|  
|<span data-ttu-id="83f03-123">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="83f03-123">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="83f03-124">`cchBuffer`má hodnotu null nebo menší než délka řetězce verze.</span><span class="sxs-lookup"><span data-stu-id="83f03-124">`cchBuffer` is null or less than the length of the version string.</span></span>|  
|<span data-ttu-id="83f03-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="83f03-125">E_NOTIMPL</span></span>|<span data-ttu-id="83f03-126">Tato metoda není k dispozici v operačním systému Microsoft Windows 95, Microsoft Windows 98 nebo Microsoft Windows Millennium Edition.</span><span class="sxs-lookup"><span data-stu-id="83f03-126">This method is not available on the Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows Millennium Edition operating system.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="83f03-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="83f03-127">Requirements</span></span>  
 <span data-ttu-id="83f03-128">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83f03-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83f03-129">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="83f03-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="83f03-130">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="83f03-130">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83f03-131">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83f03-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83f03-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="83f03-132">See also</span></span>

- [<span data-ttu-id="83f03-133">GetRequestedRuntimeInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="83f03-133">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="83f03-134">GetRequestedRuntimeVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="83f03-134">GetRequestedRuntimeVersion Function</span></span>](getrequestedruntimeversion-function.md)
- [<span data-ttu-id="83f03-135">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="83f03-135">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
