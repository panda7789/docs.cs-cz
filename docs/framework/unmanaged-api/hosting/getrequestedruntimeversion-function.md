---
title: GetRequestedRuntimeVersion – funkce
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersion
helpviewer_keywords:
- GetRequestedRuntimeVersion function [.NET Framework hosting]
ms.assetid: 82f596a4-483d-4509-b0c5-a84c53c3da1b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbc77195c3fe2581475d768b59993de274ac06a6
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490326"
---
# <a name="getrequestedruntimeversion-function"></a><span data-ttu-id="a73f5-102">GetRequestedRuntimeVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="a73f5-102">GetRequestedRuntimeVersion Function</span></span>
<span data-ttu-id="a73f5-103">Získá číslo verze common language runtime (CLR) požadované určenou aplikací.</span><span class="sxs-lookup"><span data-stu-id="a73f5-103">Gets the version number of the common language runtime (CLR) requested by the specified application.</span></span> <span data-ttu-id="a73f5-104">Pokud není nainstalována verze, získá nejnovější verzi, která je nainstalována před požadovanou verzí.</span><span class="sxs-lookup"><span data-stu-id="a73f5-104">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 <span data-ttu-id="a73f5-105">Tato funkce se již nepoužívá v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="a73f5-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a73f5-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a73f5-106">Syntax</span></span>  
  
```  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *pdwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a73f5-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="a73f5-107">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="a73f5-108">[in] Název aplikace.</span><span class="sxs-lookup"><span data-stu-id="a73f5-108">[in] The name of the application.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="a73f5-109">[out] Vyrovnávací paměť, která obsahuje řetězec, číslo verze po úspěšném dokončení.</span><span class="sxs-lookup"><span data-stu-id="a73f5-109">[out] A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="a73f5-110">[in] Délka vyrovnávací paměti verze.</span><span class="sxs-lookup"><span data-stu-id="a73f5-110">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="a73f5-111">[out] Ukazatel na délku řetězce číslo verze.</span><span class="sxs-lookup"><span data-stu-id="a73f5-111">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a73f5-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a73f5-112">Return Value</span></span>  
 <span data-ttu-id="a73f5-113">Tato metoda vrací standardní kódy chyb modelu COM (Component Object), jak je definovaný ve WinError.h, kromě následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="a73f5-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="a73f5-114">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="a73f5-114">Return code</span></span>|<span data-ttu-id="a73f5-115">Popis</span><span class="sxs-lookup"><span data-stu-id="a73f5-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="a73f5-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="a73f5-116">S_OK</span></span>|<span data-ttu-id="a73f5-117">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="a73f5-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="a73f5-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="a73f5-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="a73f5-119">Verze vyrovnávací paměť není dostatečně velký pro uložení řetězce verze.</span><span class="sxs-lookup"><span data-stu-id="a73f5-119">The version buffer is not large enough to store the version string.</span></span>|  
|<span data-ttu-id="a73f5-120">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="a73f5-120">E_POINTER</span></span>|<span data-ttu-id="a73f5-121">`pdwLength` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="a73f5-121">`pdwLength` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a73f5-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a73f5-122">Requirements</span></span>  
 <span data-ttu-id="a73f5-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a73f5-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a73f5-124">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a73f5-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a73f5-125">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a73f5-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a73f5-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a73f5-126">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a73f5-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a73f5-127">See also</span></span>

- [<span data-ttu-id="a73f5-128">GetRequestedRuntimeInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="a73f5-128">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="a73f5-129">GetVersionFromProcess – funkce</span><span class="sxs-lookup"><span data-stu-id="a73f5-129">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [<span data-ttu-id="a73f5-130">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="a73f5-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
