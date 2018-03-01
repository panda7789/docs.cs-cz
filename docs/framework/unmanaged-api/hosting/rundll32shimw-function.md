---
title: "RunDll32ShimW – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a046ed8d540b27bfb73a6e94f148d41f8ac7b264
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="rundll32shimw-function"></a><span data-ttu-id="205f3-102">RunDll32ShimW – funkce</span><span class="sxs-lookup"><span data-stu-id="205f3-102">RunDll32ShimW Function</span></span>
<span data-ttu-id="205f3-103">Provede zadaný příkaz.</span><span class="sxs-lookup"><span data-stu-id="205f3-103">Executes the specified command.</span></span>  
  
 <span data-ttu-id="205f3-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="205f3-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="205f3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="205f3-105">Syntax</span></span>  
  
```  
HRESULT RunDll32ShimW (  
    [in] HWND        hwnd,  
    [in] HINSTANCE   hinst,  
    [in] LPCWSTR     lpszCmdLine,  
    [in] int         nCmdShow  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="205f3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="205f3-106">Parameters</span></span>  
 `hwnd`  
 <span data-ttu-id="205f3-107">[v] Popisovač pro okno, ve kterém se zobrazí výstup příkazu.</span><span class="sxs-lookup"><span data-stu-id="205f3-107">[in] A handle to a window in which the command output will be displayed.</span></span>  
  
 `hinst`  
 <span data-ttu-id="205f3-108">[v] Popisovač pro knihovnu, která obsahuje příkaz.</span><span class="sxs-lookup"><span data-stu-id="205f3-108">[in] A handle to the library that contains the command.</span></span>  
  
 `lpszCmdLine`  
 <span data-ttu-id="205f3-109">[v] Řetězec, který určuje příkaz, který má být proveden.</span><span class="sxs-lookup"><span data-stu-id="205f3-109">[in] A string that specifies the command to be executed.</span></span>  
  
 `nCmdShow`  
 <span data-ttu-id="205f3-110">[v] Celé číslo, které určuje režim zobrazení pro ve výstupním okně.</span><span class="sxs-lookup"><span data-stu-id="205f3-110">[in] An integer that specifies the display mode for the output window.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="205f3-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="205f3-111">Requirements</span></span>  
 <span data-ttu-id="205f3-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="205f3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="205f3-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="205f3-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="205f3-114">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="205f3-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="205f3-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="205f3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="205f3-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="205f3-116">See Also</span></span>  
 [<span data-ttu-id="205f3-117">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="205f3-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
