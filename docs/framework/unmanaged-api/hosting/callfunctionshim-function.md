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
ms.openlocfilehash: 7aeb813cafbf5b18739c4574c386398ac3c7a77b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777998"
---
# <a name="callfunctionshim-function"></a><span data-ttu-id="4e79d-102">CallFunctionShim – funkce</span><span class="sxs-lookup"><span data-stu-id="4e79d-102">CallFunctionShim Function</span></span>
<span data-ttu-id="4e79d-103">Provede volání funkce, která má zadaný název a parametry v určené knihovně.</span><span class="sxs-lookup"><span data-stu-id="4e79d-103">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 <span data-ttu-id="4e79d-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4e79d-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e79d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e79d-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="4e79d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4e79d-106">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="4e79d-107">[in] Název knihovny obsahující tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="4e79d-107">[in] The name of the library containing the function.</span></span>  
  
 `szFunctionName`  
 <span data-ttu-id="4e79d-108">[in] Název funkce.</span><span class="sxs-lookup"><span data-stu-id="4e79d-108">[in] The name of the function.</span></span>  
  
 `lpvArgument1`  
 <span data-ttu-id="4e79d-109">[in] První argument předat do funkce.</span><span class="sxs-lookup"><span data-stu-id="4e79d-109">[in] The first argument to pass to the function.</span></span>  
  
 `lpvArgument2`  
 <span data-ttu-id="4e79d-110">[in] Druhý argument předat do funkce.</span><span class="sxs-lookup"><span data-stu-id="4e79d-110">[in] The second argument to pass to the function.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="4e79d-111">[in] Verzi knihovny, který obsahuje funkci.</span><span class="sxs-lookup"><span data-stu-id="4e79d-111">[in] The version of the library that contains the function.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="4e79d-112">[in] Vyhrazeno pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="4e79d-112">[in] Reserved for future use.</span></span> <span data-ttu-id="4e79d-113">Předání nuly v tomto parametru.</span><span class="sxs-lookup"><span data-stu-id="4e79d-113">Pass zero in this parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e79d-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4e79d-114">Requirements</span></span>  
 <span data-ttu-id="4e79d-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e79d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e79d-116">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4e79d-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4e79d-117">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4e79d-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4e79d-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e79d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e79d-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4e79d-119">See also</span></span>

- [<span data-ttu-id="4e79d-120">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="4e79d-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
