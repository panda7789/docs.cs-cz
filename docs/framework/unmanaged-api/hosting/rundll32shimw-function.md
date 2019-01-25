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
ms.openlocfilehash: 883f987eb168bf5996baba66f5081875e67f2000
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54698723"
---
# <a name="rundll32shimw-function"></a><span data-ttu-id="89eea-102">RunDll32ShimW – funkce</span><span class="sxs-lookup"><span data-stu-id="89eea-102">RunDll32ShimW Function</span></span>
<span data-ttu-id="89eea-103">Provede zadaný příkaz.</span><span class="sxs-lookup"><span data-stu-id="89eea-103">Executes the specified command.</span></span>  
  
 <span data-ttu-id="89eea-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="89eea-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89eea-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89eea-105">Syntax</span></span>  
  
```  
HRESULT RunDll32ShimW (  
    [in] HWND        hwnd,  
    [in] HINSTANCE   hinst,  
    [in] LPCWSTR     lpszCmdLine,  
    [in] int         nCmdShow  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="89eea-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="89eea-106">Parameters</span></span>  
 `hwnd`  
 <span data-ttu-id="89eea-107">[in] Popisovač okna, ve kterém se zobrazí výstup příkazu.</span><span class="sxs-lookup"><span data-stu-id="89eea-107">[in] A handle to a window in which the command output will be displayed.</span></span>  
  
 `hinst`  
 <span data-ttu-id="89eea-108">[in] Popisovač do knihovny, který obsahuje příkaz.</span><span class="sxs-lookup"><span data-stu-id="89eea-108">[in] A handle to the library that contains the command.</span></span>  
  
 `lpszCmdLine`  
 <span data-ttu-id="89eea-109">[in] Řetězec, který určuje příkaz, který se spustí.</span><span class="sxs-lookup"><span data-stu-id="89eea-109">[in] A string that specifies the command to be executed.</span></span>  
  
 `nCmdShow`  
 <span data-ttu-id="89eea-110">[in] Celé číslo, které určuje režim zobrazení v okně výstup.</span><span class="sxs-lookup"><span data-stu-id="89eea-110">[in] An integer that specifies the display mode for the output window.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89eea-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="89eea-111">Requirements</span></span>  
 <span data-ttu-id="89eea-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89eea-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89eea-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="89eea-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="89eea-114">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="89eea-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="89eea-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89eea-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89eea-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89eea-116">See also</span></span>
- [<span data-ttu-id="89eea-117">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="89eea-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
