---
title: CloseCLREnumeration – funkce
ms.date: 03/30/2017
api_name:
- CloseCLREnumeration
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CloseCLREnumeration
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CloseCLR Enumeration function
ms.assetid: 5e3c3958-80bb-43b1-a96b-dd3e6dbd9cd7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18903bd00b0a9d09365d03c155531a25dc013189
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406085"
---
# <a name="closeclrenumeration-function"></a><span data-ttu-id="73471-102">CloseCLREnumeration – funkce</span><span class="sxs-lookup"><span data-stu-id="73471-102">CloseCLREnumeration Function</span></span>
<span data-ttu-id="73471-103">Zavře všechny platné běžné jazyk runtime (CLR) pokračovat spuštění události umístěné v pole vrácené obslužné rutiny [enumerateclrs – funkce](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)a uvolní paměť pro cestu pole popisovač a řetězec.</span><span class="sxs-lookup"><span data-stu-id="73471-103">Closes any valid common language runtime (CLR) continue-startup events located in an array of handles returned by the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73471-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73471-104">Syntax</span></span>  
  
```  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="73471-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="73471-105">Parameters</span></span>  
 `pHandleArray`  
 <span data-ttu-id="73471-106">[v] Ukazatel na pole obslužných rutin událostí vrácených [enumerateclrs – funkce](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="73471-106">[in] Pointer to the array of event handles returned from the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span></span>  
  
 `pStringArray`  
 <span data-ttu-id="73471-107">[v] Ukazatel na pole CLR řetězec cesty vrácená z [enumerateclrs – funkce](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="73471-107">[in] Pointer to the array of CLR string paths returned from the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span></span>  
  
 `dwArrayLength`  
 <span data-ttu-id="73471-108">[v] DWORD, který obsahuje velikost (délka) buď `pHandleArray` nebo `pStringArray` (jde o stejný).</span><span class="sxs-lookup"><span data-stu-id="73471-108">[in] DWORD that contains the size (length) of either `pHandleArray` or `pStringArray` (they are the same).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73471-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="73471-109">Return Value</span></span>  
 <span data-ttu-id="73471-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="73471-110">S_OK</span></span>  
 <span data-ttu-id="73471-111">Obslužné rutiny otevřít [enumerateclrs – funkce](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) zavřou, a je paměť přidělená pro pole popisovač a řetězec vydání.</span><span class="sxs-lookup"><span data-stu-id="73471-111">Handles opened by the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) are closed, and memory allocated for the handle and string arrays is freed.</span></span>  
  
 <span data-ttu-id="73471-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="73471-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="73471-113">Délka `pHandleArray` neodpovídá délka, který se předává v `dwArrayLength`.</span><span class="sxs-lookup"><span data-stu-id="73471-113">The length of `pHandleArray` does not match the length that is passed in `dwArrayLength`.</span></span>  
  
 <span data-ttu-id="73471-114">E_FAIL (nebo ostatní návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="73471-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="73471-115">Funkce nelze uvolnit paměť pro `pHandleArray` a `pStringArray`.</span><span class="sxs-lookup"><span data-stu-id="73471-115">The function is unable to free the memory for `pHandleArray` and `pStringArray`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73471-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="73471-116">Requirements</span></span>  
 <span data-ttu-id="73471-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73471-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73471-118">**Záhlaví:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="73471-118">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="73471-119">**Knihovna:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="73471-119">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="73471-120">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="73471-120">**.NET Framework Versions:** 3.5 SP1</span></span>
