---
title: CallFunctionShim – funkce
ms.date: 03/30/2017
api_name:
- CallFunctionShim
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CallFunctionShim
helpviewer_keywords:
- CallfunctionShim function [.NET Framework hosting]
ms.assetid: 37118465-ddf3-41f0-bf27-335b72777e63
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1060ca140db0304c8e5667f7fdf9624b3ac2b64a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429280"
---
# <a name="callfunctionshim-function"></a><span data-ttu-id="9a9fa-102">CallFunctionShim – funkce</span><span class="sxs-lookup"><span data-stu-id="9a9fa-102">CallFunctionShim Function</span></span>
<span data-ttu-id="9a9fa-103">Zavolá funkci, která má zadaný název a parametry v určené knihovně.</span><span class="sxs-lookup"><span data-stu-id="9a9fa-103">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 <span data-ttu-id="9a9fa-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9a9fa-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a9fa-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a9fa-105">Syntax</span></span>  
  
```  
HRESULT CallFunctionShim (  
    [in] LPCWSTR     szDllName,  
    [in] LPCSTR      szFunctionName,  
    [in] LPVOID      lpvArgument1,  
    [in] LPVOID      lpvArgument2,  
    [in] LPCWSTR     szVersion,  
    [in] LPVOID      pvReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9a9fa-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9a9fa-106">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="9a9fa-107">[v] Název knihovny obsahující danou funkci.</span><span class="sxs-lookup"><span data-stu-id="9a9fa-107">[in] The name of the library containing the function.</span></span>  
  
 `szFunctionName`  
 <span data-ttu-id="9a9fa-108">[v] Název funkce.</span><span class="sxs-lookup"><span data-stu-id="9a9fa-108">[in] The name of the function.</span></span>  
  
 `lpvArgument1`  
 <span data-ttu-id="9a9fa-109">[v] První argument předat funkce.</span><span class="sxs-lookup"><span data-stu-id="9a9fa-109">[in] The first argument to pass to the function.</span></span>  
  
 `lpvArgument2`  
 <span data-ttu-id="9a9fa-110">[v] Druhý argument funkce předávání.</span><span class="sxs-lookup"><span data-stu-id="9a9fa-110">[in] The second argument to pass to the function.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="9a9fa-111">[v] Verze knihovny, která obsahuje funkci.</span><span class="sxs-lookup"><span data-stu-id="9a9fa-111">[in] The version of the library that contains the function.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="9a9fa-112">[v] Vyhrazeno pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="9a9fa-112">[in] Reserved for future use.</span></span> <span data-ttu-id="9a9fa-113">Předejte nula v tomto parametru.</span><span class="sxs-lookup"><span data-stu-id="9a9fa-113">Pass zero in this parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a9fa-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9a9fa-114">Requirements</span></span>  
 <span data-ttu-id="9a9fa-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a9fa-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a9fa-116">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9a9fa-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9a9fa-117">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9a9fa-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a9fa-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a9fa-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a9fa-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="9a9fa-119">See Also</span></span>  
 [<span data-ttu-id="9a9fa-120">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="9a9fa-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
