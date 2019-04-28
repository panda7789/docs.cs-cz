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
ms.openlocfilehash: ccfdf9ffab35f076b85c067c2b412020a5f541b2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765164"
---
# <a name="rundll32shimw-function"></a><span data-ttu-id="7d429-102">RunDll32ShimW – funkce</span><span class="sxs-lookup"><span data-stu-id="7d429-102">RunDll32ShimW Function</span></span>
<span data-ttu-id="7d429-103">Provede zadaný příkaz.</span><span class="sxs-lookup"><span data-stu-id="7d429-103">Executes the specified command.</span></span>  
  
 <span data-ttu-id="7d429-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7d429-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d429-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d429-105">Syntax</span></span>  
  
```  
HRESULT RunDll32ShimW (  
    [in] HWND        hwnd,  
    [in] HINSTANCE   hinst,  
    [in] LPCWSTR     lpszCmdLine,  
    [in] int         nCmdShow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d429-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d429-106">Parameters</span></span>  
 `hwnd`  
 <span data-ttu-id="7d429-107">[in] Popisovač okna, ve kterém se zobrazí výstup příkazu.</span><span class="sxs-lookup"><span data-stu-id="7d429-107">[in] A handle to a window in which the command output will be displayed.</span></span>  
  
 `hinst`  
 <span data-ttu-id="7d429-108">[in] Popisovač do knihovny, který obsahuje příkaz.</span><span class="sxs-lookup"><span data-stu-id="7d429-108">[in] A handle to the library that contains the command.</span></span>  
  
 `lpszCmdLine`  
 <span data-ttu-id="7d429-109">[in] Řetězec, který určuje příkaz, který se spustí.</span><span class="sxs-lookup"><span data-stu-id="7d429-109">[in] A string that specifies the command to be executed.</span></span>  
  
 `nCmdShow`  
 <span data-ttu-id="7d429-110">[in] Celé číslo, které určuje režim zobrazení v okně výstup.</span><span class="sxs-lookup"><span data-stu-id="7d429-110">[in] An integer that specifies the display mode for the output window.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d429-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d429-111">Requirements</span></span>  
 <span data-ttu-id="7d429-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d429-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d429-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7d429-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7d429-114">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7d429-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d429-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d429-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d429-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d429-116">See also</span></span>

- [<span data-ttu-id="7d429-117">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="7d429-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
