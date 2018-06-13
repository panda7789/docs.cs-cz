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
ms.openlocfilehash: 18247a947449ea5fd19f1882031b598086332742
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441737"
---
# <a name="rundll32shimw-function"></a><span data-ttu-id="2e47e-102">RunDll32ShimW – funkce</span><span class="sxs-lookup"><span data-stu-id="2e47e-102">RunDll32ShimW Function</span></span>
<span data-ttu-id="2e47e-103">Provede zadaný příkaz.</span><span class="sxs-lookup"><span data-stu-id="2e47e-103">Executes the specified command.</span></span>  
  
 <span data-ttu-id="2e47e-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e47e-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e47e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e47e-105">Syntax</span></span>  
  
```  
HRESULT RunDll32ShimW (  
    [in] HWND        hwnd,  
    [in] HINSTANCE   hinst,  
    [in] LPCWSTR     lpszCmdLine,  
    [in] int         nCmdShow  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2e47e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2e47e-106">Parameters</span></span>  
 `hwnd`  
 <span data-ttu-id="2e47e-107">[v] Popisovač pro okno, ve kterém se zobrazí výstup příkazu.</span><span class="sxs-lookup"><span data-stu-id="2e47e-107">[in] A handle to a window in which the command output will be displayed.</span></span>  
  
 `hinst`  
 <span data-ttu-id="2e47e-108">[v] Popisovač pro knihovnu, která obsahuje příkaz.</span><span class="sxs-lookup"><span data-stu-id="2e47e-108">[in] A handle to the library that contains the command.</span></span>  
  
 `lpszCmdLine`  
 <span data-ttu-id="2e47e-109">[v] Řetězec, který určuje příkaz, který má být proveden.</span><span class="sxs-lookup"><span data-stu-id="2e47e-109">[in] A string that specifies the command to be executed.</span></span>  
  
 `nCmdShow`  
 <span data-ttu-id="2e47e-110">[v] Celé číslo, které určuje režim zobrazení pro ve výstupním okně.</span><span class="sxs-lookup"><span data-stu-id="2e47e-110">[in] An integer that specifies the display mode for the output window.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e47e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2e47e-111">Requirements</span></span>  
 <span data-ttu-id="2e47e-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e47e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e47e-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2e47e-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2e47e-114">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2e47e-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2e47e-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e47e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e47e-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="2e47e-116">See Also</span></span>  
 [<span data-ttu-id="2e47e-117">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="2e47e-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
