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
ms.openlocfilehash: 60b6d9c302cd3af9f41e5a8dce62d7eb268c4198
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61961171"
---
# <a name="closeclrenumeration-function"></a><span data-ttu-id="764cd-102">CloseCLREnumeration – funkce</span><span class="sxs-lookup"><span data-stu-id="764cd-102">CloseCLREnumeration Function</span></span>
<span data-ttu-id="764cd-103">Zavře žádné platný common language runtime (CLR) pokračovat po spuštění události nachází v poli popisovačů vrácený [enumerateclrs – funkce](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)a uvolní paměť pro cestu pole popisovač a řetězce.</span><span class="sxs-lookup"><span data-stu-id="764cd-103">Closes any valid common language runtime (CLR) continue-startup events located in an array of handles returned by the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="764cd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="764cd-104">Syntax</span></span>  
  
```  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="764cd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="764cd-105">Parameters</span></span>  
 `pHandleArray`  
 <span data-ttu-id="764cd-106">[in] Ukazatel na pole obslužné rutiny událostí vrácených [enumerateclrs – funkce](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="764cd-106">[in] Pointer to the array of event handles returned from the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span></span>  
  
 `pStringArray`  
 <span data-ttu-id="764cd-107">[in] Ukazatel na pole vrácená z cesty řetězce CLR [enumerateclrs – funkce](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="764cd-107">[in] Pointer to the array of CLR string paths returned from the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span></span>  
  
 `dwArrayLength`  
 <span data-ttu-id="764cd-108">[in] DWORD, který obsahuje velikost (délka) buď `pHandleArray` nebo `pStringArray` (jsou stejné).</span><span class="sxs-lookup"><span data-stu-id="764cd-108">[in] DWORD that contains the size (length) of either `pHandleArray` or `pStringArray` (they are the same).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="764cd-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="764cd-109">Return Value</span></span>  
 <span data-ttu-id="764cd-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="764cd-110">S_OK</span></span>  
 <span data-ttu-id="764cd-111">Popisovače otevírány [enumerateclrs – funkce](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) zavřou, a je uvolněna paměť přidělená pro řetězec a popisovače pole.</span><span class="sxs-lookup"><span data-stu-id="764cd-111">Handles opened by the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) are closed, and memory allocated for the handle and string arrays is freed.</span></span>  
  
 <span data-ttu-id="764cd-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="764cd-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="764cd-113">Délka `pHandleArray` neodpovídá délce, které je předáno `dwArrayLength`.</span><span class="sxs-lookup"><span data-stu-id="764cd-113">The length of `pHandleArray` does not match the length that is passed in `dwArrayLength`.</span></span>  
  
 <span data-ttu-id="764cd-114">E_FAIL (nebo jiné E_ návratové kódy)</span><span class="sxs-lookup"><span data-stu-id="764cd-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="764cd-115">Nelze uvolnit paměť pro funkci `pHandleArray` a `pStringArray`.</span><span class="sxs-lookup"><span data-stu-id="764cd-115">The function is unable to free the memory for `pHandleArray` and `pStringArray`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="764cd-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="764cd-116">Requirements</span></span>  
 <span data-ttu-id="764cd-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="764cd-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="764cd-118">**Záhlaví:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="764cd-118">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="764cd-119">**Knihovna:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="764cd-119">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="764cd-120">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="764cd-120">**.NET Framework Versions:** 3.5 SP1</span></span>
