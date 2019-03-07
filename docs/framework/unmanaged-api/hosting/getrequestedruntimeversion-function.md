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
ms.openlocfilehash: 87728ea52bc257920041acc2e2ecfc040cdbbfb0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471794"
---
# <a name="getrequestedruntimeversion-function"></a><span data-ttu-id="26a80-102">GetRequestedRuntimeVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="26a80-102">GetRequestedRuntimeVersion Function</span></span>
<span data-ttu-id="26a80-103">Získá číslo verze common language runtime (CLR) požadované určenou aplikací.</span><span class="sxs-lookup"><span data-stu-id="26a80-103">Gets the version number of the common language runtime (CLR) requested by the specified application.</span></span> <span data-ttu-id="26a80-104">Pokud není nainstalována verze, získá nejnovější verzi, která je nainstalována před požadovanou verzí.</span><span class="sxs-lookup"><span data-stu-id="26a80-104">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 <span data-ttu-id="26a80-105">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="26a80-105">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26a80-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26a80-106">Syntax</span></span>  
  
```  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *pdwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26a80-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="26a80-107">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="26a80-108">[in] Název aplikace.</span><span class="sxs-lookup"><span data-stu-id="26a80-108">[in] The name of the application.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="26a80-109">[out] Vyrovnávací paměť, která obsahuje řetězec, číslo verze po úspěšném dokončení.</span><span class="sxs-lookup"><span data-stu-id="26a80-109">[out] A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="26a80-110">[in] Délka vyrovnávací paměti verze.</span><span class="sxs-lookup"><span data-stu-id="26a80-110">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="26a80-111">[out] Ukazatel na délku řetězce číslo verze.</span><span class="sxs-lookup"><span data-stu-id="26a80-111">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="26a80-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="26a80-112">Return Value</span></span>  
 <span data-ttu-id="26a80-113">Tato metoda vrací standardní kódy chyb modelu COM (Component Object), jak je definovaný ve WinError.h, kromě následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="26a80-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="26a80-114">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="26a80-114">Return code</span></span>|<span data-ttu-id="26a80-115">Popis</span><span class="sxs-lookup"><span data-stu-id="26a80-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="26a80-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="26a80-116">S_OK</span></span>|<span data-ttu-id="26a80-117">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="26a80-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="26a80-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="26a80-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="26a80-119">Verze vyrovnávací paměť není dostatečně velký pro uložení řetězce verze.</span><span class="sxs-lookup"><span data-stu-id="26a80-119">The version buffer is not large enough to store the version string.</span></span>|  
|<span data-ttu-id="26a80-120">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="26a80-120">E_POINTER</span></span>|<span data-ttu-id="26a80-121">`pdwLength` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="26a80-121">`pdwLength` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="26a80-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="26a80-122">Requirements</span></span>  
 <span data-ttu-id="26a80-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26a80-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26a80-124">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="26a80-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="26a80-125">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="26a80-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="26a80-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26a80-126">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26a80-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="26a80-127">See also</span></span>
- [<span data-ttu-id="26a80-128">GetRequestedRuntimeInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="26a80-128">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="26a80-129">GetVersionFromProcess – funkce</span><span class="sxs-lookup"><span data-stu-id="26a80-129">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [<span data-ttu-id="26a80-130">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="26a80-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
