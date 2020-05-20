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
ms.openlocfilehash: b7a38d28b55842e9358bd9c7019b84c529526613
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617162"
---
# <a name="getrequestedruntimeversion-function"></a><span data-ttu-id="40977-102">GetRequestedRuntimeVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="40977-102">GetRequestedRuntimeVersion Function</span></span>
<span data-ttu-id="40977-103">Získá číslo verze modulu CLR (Common Language Runtime), který požaduje Zadaná aplikace.</span><span class="sxs-lookup"><span data-stu-id="40977-103">Gets the version number of the common language runtime (CLR) requested by the specified application.</span></span> <span data-ttu-id="40977-104">Pokud tato verze není nainstalovaná, získá nejnovější verzi, která je nainstalovaná před požadovanou verzí.</span><span class="sxs-lookup"><span data-stu-id="40977-104">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 <span data-ttu-id="40977-105">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="40977-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40977-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40977-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *pdwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40977-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="40977-107">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="40977-108">pro Název aplikace</span><span class="sxs-lookup"><span data-stu-id="40977-108">[in] The name of the application.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="40977-109">mimo Vyrovnávací paměť, která obsahuje řetězec čísla verze po úspěšném dokončení.</span><span class="sxs-lookup"><span data-stu-id="40977-109">[out] A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="40977-110">pro Délka vyrovnávací paměti verze.</span><span class="sxs-lookup"><span data-stu-id="40977-110">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="40977-111">mimo Ukazatel na délku řetězce čísla verze.</span><span class="sxs-lookup"><span data-stu-id="40977-111">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="40977-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="40977-112">Return Value</span></span>  
 <span data-ttu-id="40977-113">Tato metoda vrátí standardní kódy chyb modelu COM (Component Object Model), jak je definováno v WinError. h, kromě následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="40977-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="40977-114">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="40977-114">Return code</span></span>|<span data-ttu-id="40977-115">Popis</span><span class="sxs-lookup"><span data-stu-id="40977-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="40977-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="40977-116">S_OK</span></span>|<span data-ttu-id="40977-117">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="40977-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="40977-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="40977-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="40977-119">Vyrovnávací paměť verze není dostatečně velká pro uložení řetězce verze.</span><span class="sxs-lookup"><span data-stu-id="40977-119">The version buffer is not large enough to store the version string.</span></span>|  
|<span data-ttu-id="40977-120">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="40977-120">E_POINTER</span></span>|<span data-ttu-id="40977-121">`pdwLength`má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="40977-121">`pdwLength` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="40977-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="40977-122">Requirements</span></span>  
 <span data-ttu-id="40977-123">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40977-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40977-124">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="40977-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="40977-125">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="40977-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="40977-126">**Verze .NET Framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40977-126">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40977-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="40977-127">See also</span></span>

- [<span data-ttu-id="40977-128">GetRequestedRuntimeInfo – funkce</span><span class="sxs-lookup"><span data-stu-id="40977-128">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="40977-129">GetVersionFromProcess – funkce</span><span class="sxs-lookup"><span data-stu-id="40977-129">GetVersionFromProcess Function</span></span>](getversionfromprocess-function.md)
- [<span data-ttu-id="40977-130">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="40977-130">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
