---
title: RunDll32ShimW – funkce
ms.date: 03/30/2017
api_name:
- RunDll32ShimW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- RunDll32ShimW
helpviewer_keywords:
- RunDll32ShimW function [.NET Framework hosting]
ms.assetid: 9ea07b57-96e2-44df-8711-8fe6c119087f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 336fba6defc00eb87fcfa7e6b1aaafa0fcb15691
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494204"
---
# <a name="rundll32shimw-function"></a><span data-ttu-id="6e2ce-102">RunDll32ShimW – funkce</span><span class="sxs-lookup"><span data-stu-id="6e2ce-102">RunDll32ShimW Function</span></span>
<span data-ttu-id="6e2ce-103">Provede zadaný příkaz.</span><span class="sxs-lookup"><span data-stu-id="6e2ce-103">Executes the specified command.</span></span>  
  
 <span data-ttu-id="6e2ce-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6e2ce-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e2ce-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e2ce-105">Syntax</span></span>  
  
```  
HRESULT RunDll32ShimW (  
    [in] HWND        hwnd,  
    [in] HINSTANCE   hinst,  
    [in] LPCWSTR     lpszCmdLine,  
    [in] int         nCmdShow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e2ce-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6e2ce-106">Parameters</span></span>  
 `hwnd`  
 <span data-ttu-id="6e2ce-107">[in] Popisovač okna, ve kterém se zobrazí výstup příkazu.</span><span class="sxs-lookup"><span data-stu-id="6e2ce-107">[in] A handle to a window in which the command output will be displayed.</span></span>  
  
 `hinst`  
 <span data-ttu-id="6e2ce-108">[in] Popisovač do knihovny, který obsahuje příkaz.</span><span class="sxs-lookup"><span data-stu-id="6e2ce-108">[in] A handle to the library that contains the command.</span></span>  
  
 `lpszCmdLine`  
 <span data-ttu-id="6e2ce-109">[in] Řetězec, který určuje příkaz, který se spustí.</span><span class="sxs-lookup"><span data-stu-id="6e2ce-109">[in] A string that specifies the command to be executed.</span></span>  
  
 `nCmdShow`  
 <span data-ttu-id="6e2ce-110">[in] Celé číslo, které určuje režim zobrazení v okně výstup.</span><span class="sxs-lookup"><span data-stu-id="6e2ce-110">[in] An integer that specifies the display mode for the output window.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e2ce-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6e2ce-111">Requirements</span></span>  
 <span data-ttu-id="6e2ce-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e2ce-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e2ce-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6e2ce-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6e2ce-114">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6e2ce-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6e2ce-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e2ce-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e2ce-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e2ce-116">See also</span></span>
- [<span data-ttu-id="6e2ce-117">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="6e2ce-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
