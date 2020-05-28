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
ms.openlocfilehash: 90304eb94e6f53d3132c97f5ababdc45f6053d7c
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006568"
---
# <a name="rundll32shimw-function"></a><span data-ttu-id="709c4-102">RunDll32ShimW – funkce</span><span class="sxs-lookup"><span data-stu-id="709c4-102">RunDll32ShimW Function</span></span>
<span data-ttu-id="709c4-103">Provede zadaný příkaz.</span><span class="sxs-lookup"><span data-stu-id="709c4-103">Executes the specified command.</span></span>  
  
 <span data-ttu-id="709c4-104">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="709c4-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="709c4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="709c4-105">Syntax</span></span>  
  
```cpp  
HRESULT RunDll32ShimW (  
    [in] HWND        hwnd,  
    [in] HINSTANCE   hinst,  
    [in] LPCWSTR     lpszCmdLine,  
    [in] int         nCmdShow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="709c4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="709c4-106">Parameters</span></span>  
 `hwnd`  
 <span data-ttu-id="709c4-107">pro Popisovač okna, ve kterém se zobrazí výstup příkazu.</span><span class="sxs-lookup"><span data-stu-id="709c4-107">[in] A handle to a window in which the command output will be displayed.</span></span>  
  
 `hinst`  
 <span data-ttu-id="709c4-108">pro Popisovač knihovny, která obsahuje příkaz.</span><span class="sxs-lookup"><span data-stu-id="709c4-108">[in] A handle to the library that contains the command.</span></span>  
  
 `lpszCmdLine`  
 <span data-ttu-id="709c4-109">pro Řetězec, který určuje příkaz, který má být spuštěn.</span><span class="sxs-lookup"><span data-stu-id="709c4-109">[in] A string that specifies the command to be executed.</span></span>  
  
 `nCmdShow`  
 <span data-ttu-id="709c4-110">pro Celé číslo, které určuje režim zobrazení okna výstup.</span><span class="sxs-lookup"><span data-stu-id="709c4-110">[in] An integer that specifies the display mode for the output window.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="709c4-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="709c4-111">Requirements</span></span>  
 <span data-ttu-id="709c4-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="709c4-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="709c4-113">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="709c4-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="709c4-114">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="709c4-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="709c4-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="709c4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="709c4-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="709c4-116">See also</span></span>

- [<span data-ttu-id="709c4-117">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="709c4-117">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
