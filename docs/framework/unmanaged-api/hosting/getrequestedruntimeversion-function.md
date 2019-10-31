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
ms.openlocfilehash: be7d6ce29a9c9c4e3e530df40432b1a4c3b2d389
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136347"
---
# <a name="getrequestedruntimeversion-function"></a><span data-ttu-id="13a68-102">GetRequestedRuntimeVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="13a68-102">GetRequestedRuntimeVersion Function</span></span>
<span data-ttu-id="13a68-103">Získá číslo verze modulu CLR (Common Language Runtime), který požaduje Zadaná aplikace.</span><span class="sxs-lookup"><span data-stu-id="13a68-103">Gets the version number of the common language runtime (CLR) requested by the specified application.</span></span> <span data-ttu-id="13a68-104">Pokud tato verze není nainstalovaná, získá nejnovější verzi, která je nainstalovaná před požadovanou verzí.</span><span class="sxs-lookup"><span data-stu-id="13a68-104">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 <span data-ttu-id="13a68-105">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="13a68-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13a68-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13a68-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *pdwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13a68-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="13a68-107">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="13a68-108">pro Název aplikace</span><span class="sxs-lookup"><span data-stu-id="13a68-108">[in] The name of the application.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="13a68-109">mimo Vyrovnávací paměť, která obsahuje řetězec čísla verze po úspěšném dokončení.</span><span class="sxs-lookup"><span data-stu-id="13a68-109">[out] A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="13a68-110">pro Délka vyrovnávací paměti verze.</span><span class="sxs-lookup"><span data-stu-id="13a68-110">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="13a68-111">mimo Ukazatel na délku řetězce čísla verze.</span><span class="sxs-lookup"><span data-stu-id="13a68-111">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13a68-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="13a68-112">Return Value</span></span>  
 <span data-ttu-id="13a68-113">Tato metoda vrátí standardní kódy chyb modelu COM (Component Object Model), jak je definováno v WinError. h, kromě následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="13a68-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="13a68-114">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="13a68-114">Return code</span></span>|<span data-ttu-id="13a68-115">Popis</span><span class="sxs-lookup"><span data-stu-id="13a68-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="13a68-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="13a68-116">S_OK</span></span>|<span data-ttu-id="13a68-117">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="13a68-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="13a68-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="13a68-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="13a68-119">Vyrovnávací paměť verze není dostatečně velká pro uložení řetězce verze.</span><span class="sxs-lookup"><span data-stu-id="13a68-119">The version buffer is not large enough to store the version string.</span></span>|  
|<span data-ttu-id="13a68-120">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="13a68-120">E_POINTER</span></span>|<span data-ttu-id="13a68-121">`pdwLength` je null.</span><span class="sxs-lookup"><span data-stu-id="13a68-121">`pdwLength` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="13a68-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="13a68-122">Requirements</span></span>  
 <span data-ttu-id="13a68-123">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13a68-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13a68-124">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="13a68-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="13a68-125">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="13a68-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="13a68-126">**Verze .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13a68-126">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13a68-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="13a68-127">See also</span></span>

- [<span data-ttu-id="13a68-128">GetRequestedRuntimeInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="13a68-128">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="13a68-129">GetVersionFromProcess – funkce</span><span class="sxs-lookup"><span data-stu-id="13a68-129">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [<span data-ttu-id="13a68-130">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="13a68-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
