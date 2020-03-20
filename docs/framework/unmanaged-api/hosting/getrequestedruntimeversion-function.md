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
ms.openlocfilehash: 6be0bc5d08f612dcb8ed7d256711e0c4367b9274
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178141"
---
# <a name="getrequestedruntimeversion-function"></a><span data-ttu-id="63f70-102">GetRequestedRuntimeVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="63f70-102">GetRequestedRuntimeVersion Function</span></span>
<span data-ttu-id="63f70-103">Získá číslo verze cltime společného jazyka (CLR) požadované zadané aplikace.</span><span class="sxs-lookup"><span data-stu-id="63f70-103">Gets the version number of the common language runtime (CLR) requested by the specified application.</span></span> <span data-ttu-id="63f70-104">Pokud tato verze není nainstalována, získá nejnovější verzi, která je nainstalována před požadovanou verzi.</span><span class="sxs-lookup"><span data-stu-id="63f70-104">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 <span data-ttu-id="63f70-105">Tato funkce byla v rozhraní .NET Framework 4 zastaralá.</span><span class="sxs-lookup"><span data-stu-id="63f70-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63f70-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63f70-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *pdwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63f70-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="63f70-107">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="63f70-108">[v] Název aplikace.</span><span class="sxs-lookup"><span data-stu-id="63f70-108">[in] The name of the application.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="63f70-109">[out] Vyrovnávací paměť, která obsahuje řetězec číslo verze po úspěšném dokončení.</span><span class="sxs-lookup"><span data-stu-id="63f70-109">[out] A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="63f70-110">[v] Délka vyrovnávací paměti verze.</span><span class="sxs-lookup"><span data-stu-id="63f70-110">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="63f70-111">[out] Ukazatel na délku řetězce čísla verze.</span><span class="sxs-lookup"><span data-stu-id="63f70-111">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63f70-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="63f70-112">Return Value</span></span>  
 <span data-ttu-id="63f70-113">Tato metoda vrátí standardní kódy chybový model COM (COM), jak je definováno v souboru WinError.h, kromě následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="63f70-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="63f70-114">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="63f70-114">Return code</span></span>|<span data-ttu-id="63f70-115">Popis</span><span class="sxs-lookup"><span data-stu-id="63f70-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="63f70-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="63f70-116">S_OK</span></span>|<span data-ttu-id="63f70-117">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="63f70-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="63f70-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="63f70-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="63f70-119">Vyrovnávací paměť verze není dostatečně velká pro uložení řetězce verze.</span><span class="sxs-lookup"><span data-stu-id="63f70-119">The version buffer is not large enough to store the version string.</span></span>|  
|<span data-ttu-id="63f70-120">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="63f70-120">E_POINTER</span></span>|<span data-ttu-id="63f70-121">`pdwLength`je null.</span><span class="sxs-lookup"><span data-stu-id="63f70-121">`pdwLength` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="63f70-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="63f70-122">Requirements</span></span>  
 <span data-ttu-id="63f70-123">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63f70-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63f70-124">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="63f70-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="63f70-125">**Knihovna:** Soubor MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="63f70-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="63f70-126">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63f70-126">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63f70-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="63f70-127">See also</span></span>

- [<span data-ttu-id="63f70-128">GetRequestedRuntimeInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="63f70-128">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="63f70-129">GetVersionFromProcess – funkce</span><span class="sxs-lookup"><span data-stu-id="63f70-129">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [<span data-ttu-id="63f70-130">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="63f70-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
