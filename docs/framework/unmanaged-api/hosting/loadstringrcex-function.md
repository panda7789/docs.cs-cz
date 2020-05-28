---
title: LoadStringRCEx – funkce
ms.date: 03/30/2017
api_name:
- LoadStringRCEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRCEx
helpviewer_keywords:
- LoadStringRCEx function [.NET Framework hosting]
ms.assetid: bc789636-ca14-4f07-8f77-9305874d7495
topic_type:
- apiref
ms.openlocfilehash: a05cbe985c2cfebb67756fdfb54398b36e87f441
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008508"
---
# <a name="loadstringrcex-function"></a><span data-ttu-id="2783e-102">LoadStringRCEx – funkce</span><span class="sxs-lookup"><span data-stu-id="2783e-102">LoadStringRCEx Function</span></span>
<span data-ttu-id="2783e-103">Přeloží hodnotu HRESULT na příslušnou chybovou zprávu pro zadanou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="2783e-103">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="2783e-104">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="2783e-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2783e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2783e-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadStringRCEx (  
    [in]  LCID    lcid,
    [in]  UINT    iResouceID,
    [out] LPWSTR  szBuffer,
    [in]  int     iMax,
    [in]  int     bQuiet,
    [out] int    *pcwchUsed  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2783e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2783e-106">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="2783e-107">pro Identifikátor jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="2783e-107">[in] A culture identifier.</span></span> <span data-ttu-id="2783e-108">Pass-1 pro `lcid` použití výchozí jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="2783e-108">Pass -1 for `lcid` to use the default culture.</span></span>  
  
 `iResourceID`  
 <span data-ttu-id="2783e-109">pro HRESULT.</span><span class="sxs-lookup"><span data-stu-id="2783e-109">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="2783e-110">mimo Vyrovnávací paměť, která obsahuje chybovou zprávu po úspěšném dokončení.</span><span class="sxs-lookup"><span data-stu-id="2783e-110">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="2783e-111">pro Velikost vyrovnávací paměti chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="2783e-111">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="2783e-112">pro Přeskočen.</span><span class="sxs-lookup"><span data-stu-id="2783e-112">[in] Ignored.</span></span>  
  
 `pcwchUsed`  
 <span data-ttu-id="2783e-113">mimo Ukazatel na délku chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="2783e-113">[out] A pointer to the length of the error message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2783e-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2783e-114">Return Value</span></span>  
 <span data-ttu-id="2783e-115">Tato metoda vrací standardní chybové kódy modelu COM, jak jsou definovány v WinError. h, kromě následujících hodnot.</span><span class="sxs-lookup"><span data-stu-id="2783e-115">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="2783e-116">Návratový kód</span><span class="sxs-lookup"><span data-stu-id="2783e-116">Return code</span></span>|<span data-ttu-id="2783e-117">Description</span><span class="sxs-lookup"><span data-stu-id="2783e-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="2783e-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="2783e-118">S_OK</span></span>|<span data-ttu-id="2783e-119">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="2783e-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="2783e-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="2783e-120">E_INVALIDARG</span></span>|<span data-ttu-id="2783e-121">`szBuffer`má hodnotu null nebo `iMax` je nula (0).</span><span class="sxs-lookup"><span data-stu-id="2783e-121">`szBuffer` is null, or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2783e-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2783e-122">Remarks</span></span>  
 <span data-ttu-id="2783e-123">Pokud metoda není úspěšně dokončena, `szBuffer` obsahuje prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="2783e-123">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2783e-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2783e-124">Requirements</span></span>  
 <span data-ttu-id="2783e-125">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2783e-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2783e-126">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2783e-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2783e-127">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2783e-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2783e-128">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2783e-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2783e-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="2783e-129">See also</span></span>

- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [<span data-ttu-id="2783e-130">LoadStringRC – funkce</span><span class="sxs-lookup"><span data-stu-id="2783e-130">LoadStringRC Function</span></span>](loadstringrc-function.md)
- [<span data-ttu-id="2783e-131">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="2783e-131">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
