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
ms.openlocfilehash: 31d93ac427ec67726c9456d623aeb683c9029ccd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773772"
---
# <a name="callfunctionshim-function"></a><span data-ttu-id="50b0c-102">CallFunctionShim – funkce</span><span class="sxs-lookup"><span data-stu-id="50b0c-102">CallFunctionShim Function</span></span>
<span data-ttu-id="50b0c-103">Provede volání funkce, která má zadaný název a parametry v určené knihovně.</span><span class="sxs-lookup"><span data-stu-id="50b0c-103">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 <span data-ttu-id="50b0c-104">Tato funkce se již nepoužívá v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="50b0c-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50b0c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50b0c-105">Syntax</span></span>  
  
```cpp  
HRESULT CallFunctionShim (  
    [in] LPCWSTR     szDllName,  
    [in] LPCSTR      szFunctionName,  
    [in] LPVOID      lpvArgument1,  
    [in] LPVOID      lpvArgument2,  
    [in] LPCWSTR     szVersion,  
    [in] LPVOID      pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50b0c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="50b0c-106">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="50b0c-107">[in] Název knihovny obsahující tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="50b0c-107">[in] The name of the library containing the function.</span></span>  
  
 `szFunctionName`  
 <span data-ttu-id="50b0c-108">[in] Název funkce.</span><span class="sxs-lookup"><span data-stu-id="50b0c-108">[in] The name of the function.</span></span>  
  
 `lpvArgument1`  
 <span data-ttu-id="50b0c-109">[in] První argument předat do funkce.</span><span class="sxs-lookup"><span data-stu-id="50b0c-109">[in] The first argument to pass to the function.</span></span>  
  
 `lpvArgument2`  
 <span data-ttu-id="50b0c-110">[in] Druhý argument předat do funkce.</span><span class="sxs-lookup"><span data-stu-id="50b0c-110">[in] The second argument to pass to the function.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="50b0c-111">[in] Verzi knihovny, který obsahuje funkci.</span><span class="sxs-lookup"><span data-stu-id="50b0c-111">[in] The version of the library that contains the function.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="50b0c-112">[in] Vyhrazeno pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="50b0c-112">[in] Reserved for future use.</span></span> <span data-ttu-id="50b0c-113">Předání nuly v tomto parametru.</span><span class="sxs-lookup"><span data-stu-id="50b0c-113">Pass zero in this parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50b0c-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="50b0c-114">Requirements</span></span>  
 <span data-ttu-id="50b0c-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50b0c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50b0c-116">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="50b0c-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="50b0c-117">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="50b0c-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50b0c-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50b0c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50b0c-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50b0c-119">See also</span></span>

- [<span data-ttu-id="50b0c-120">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="50b0c-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
