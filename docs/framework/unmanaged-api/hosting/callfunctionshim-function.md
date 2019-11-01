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
ms.openlocfilehash: d39e15a2ba71ba0c0147482259f5618dcb5d298b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192096"
---
# <a name="callfunctionshim-function"></a><span data-ttu-id="f97e6-102">CallFunctionShim – funkce</span><span class="sxs-lookup"><span data-stu-id="f97e6-102">CallFunctionShim Function</span></span>
<span data-ttu-id="f97e6-103">Provede volání funkce, která má zadaný název a parametry v zadané knihovně.</span><span class="sxs-lookup"><span data-stu-id="f97e6-103">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 <span data-ttu-id="f97e6-104">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="f97e6-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f97e6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f97e6-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="f97e6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f97e6-106">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="f97e6-107">pro Název knihovny obsahující funkci.</span><span class="sxs-lookup"><span data-stu-id="f97e6-107">[in] The name of the library containing the function.</span></span>  
  
 `szFunctionName`  
 <span data-ttu-id="f97e6-108">pro Název funkce</span><span class="sxs-lookup"><span data-stu-id="f97e6-108">[in] The name of the function.</span></span>  
  
 `lpvArgument1`  
 <span data-ttu-id="f97e6-109">pro První argument, který se má předat funkci.</span><span class="sxs-lookup"><span data-stu-id="f97e6-109">[in] The first argument to pass to the function.</span></span>  
  
 `lpvArgument2`  
 <span data-ttu-id="f97e6-110">pro Druhý argument, který se má předat funkci.</span><span class="sxs-lookup"><span data-stu-id="f97e6-110">[in] The second argument to pass to the function.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="f97e6-111">pro Verze knihovny, která obsahuje funkci.</span><span class="sxs-lookup"><span data-stu-id="f97e6-111">[in] The version of the library that contains the function.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="f97e6-112">pro Vyhrazeno pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="f97e6-112">[in] Reserved for future use.</span></span> <span data-ttu-id="f97e6-113">V tomto parametru předejte nula.</span><span class="sxs-lookup"><span data-stu-id="f97e6-113">Pass zero in this parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f97e6-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f97e6-114">Requirements</span></span>  
 <span data-ttu-id="f97e6-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f97e6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f97e6-116">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f97e6-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f97e6-117">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f97e6-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f97e6-118">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f97e6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f97e6-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f97e6-119">See also</span></span>

- [<span data-ttu-id="f97e6-120">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="f97e6-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
