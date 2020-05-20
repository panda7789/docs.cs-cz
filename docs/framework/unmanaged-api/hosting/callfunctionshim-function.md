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
ms.openlocfilehash: e8945d40a3761ec51a73a8ae90ddc1d84ccab651
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616863"
---
# <a name="callfunctionshim-function"></a><span data-ttu-id="1a922-102">CallFunctionShim – funkce</span><span class="sxs-lookup"><span data-stu-id="1a922-102">CallFunctionShim Function</span></span>
<span data-ttu-id="1a922-103">Provede volání funkce, která má zadaný název a parametry v zadané knihovně.</span><span class="sxs-lookup"><span data-stu-id="1a922-103">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 <span data-ttu-id="1a922-104">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="1a922-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a922-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a922-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="1a922-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1a922-106">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="1a922-107">pro Název knihovny obsahující funkci.</span><span class="sxs-lookup"><span data-stu-id="1a922-107">[in] The name of the library containing the function.</span></span>  
  
 `szFunctionName`  
 <span data-ttu-id="1a922-108">pro Název funkce</span><span class="sxs-lookup"><span data-stu-id="1a922-108">[in] The name of the function.</span></span>  
  
 `lpvArgument1`  
 <span data-ttu-id="1a922-109">pro První argument, který se má předat funkci.</span><span class="sxs-lookup"><span data-stu-id="1a922-109">[in] The first argument to pass to the function.</span></span>  
  
 `lpvArgument2`  
 <span data-ttu-id="1a922-110">pro Druhý argument, který se má předat funkci.</span><span class="sxs-lookup"><span data-stu-id="1a922-110">[in] The second argument to pass to the function.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="1a922-111">pro Verze knihovny, která obsahuje funkci.</span><span class="sxs-lookup"><span data-stu-id="1a922-111">[in] The version of the library that contains the function.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="1a922-112">pro Vyhrazeno pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="1a922-112">[in] Reserved for future use.</span></span> <span data-ttu-id="1a922-113">V tomto parametru předejte nula.</span><span class="sxs-lookup"><span data-stu-id="1a922-113">Pass zero in this parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a922-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1a922-114">Requirements</span></span>  
 <span data-ttu-id="1a922-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a922-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a922-116">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1a922-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1a922-117">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1a922-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1a922-118">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a922-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a922-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="1a922-119">See also</span></span>

- [<span data-ttu-id="1a922-120">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="1a922-120">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
