---
title: "CloseCLREnumeration – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CloseCLREnumeration
api_location: dbgshim.dll
api_type: COM
f1_keywords: CloseCLREnumeration
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CloseCLR Enumeration function
ms.assetid: 5e3c3958-80bb-43b1-a96b-dd3e6dbd9cd7
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2f6de2d1625b4d9f66ec27ad7ed3e6ba33cc59b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="closeclrenumeration-function"></a><span data-ttu-id="7b7e8-102">CloseCLREnumeration – funkce</span><span class="sxs-lookup"><span data-stu-id="7b7e8-102">CloseCLREnumeration Function</span></span>
<span data-ttu-id="7b7e8-103">Zavře všechny platné běžné jazyk runtime (CLR) pokračovat spuštění události umístěné v pole vrácené obslužné rutiny [enumerateclrs – funkce](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)a uvolní paměť pro cestu pole popisovač a řetězec.</span><span class="sxs-lookup"><span data-stu-id="7b7e8-103">Closes any valid common language runtime (CLR) continue-startup events located in an array of handles returned by the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b7e8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b7e8-104">Syntax</span></span>  
  
```  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7b7e8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7b7e8-105">Parameters</span></span>  
 `pHandleArray`  
 <span data-ttu-id="7b7e8-106">[v] Ukazatel na pole obslužných rutin událostí vrácených [enumerateclrs – funkce](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="7b7e8-106">[in] Pointer to the array of event handles returned from the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span></span>  
  
 `pStringArray`  
 <span data-ttu-id="7b7e8-107">[v] Ukazatel na pole CLR řetězec cesty vrácená z [enumerateclrs – funkce](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="7b7e8-107">[in] Pointer to the array of CLR string paths returned from the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span></span>  
  
 `dwArrayLength`  
 <span data-ttu-id="7b7e8-108">[v] DWORD, který obsahuje velikost (délka) buď `pHandleArray` nebo `pStringArray` (jde o stejný).</span><span class="sxs-lookup"><span data-stu-id="7b7e8-108">[in] DWORD that contains the size (length) of either `pHandleArray` or `pStringArray` (they are the same).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7b7e8-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7b7e8-109">Return Value</span></span>  
 <span data-ttu-id="7b7e8-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7b7e8-110">S_OK</span></span>  
 <span data-ttu-id="7b7e8-111">Obslužné rutiny otevřít [enumerateclrs – funkce](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) zavřou, a je paměť přidělená pro pole popisovač a řetězec vydání.</span><span class="sxs-lookup"><span data-stu-id="7b7e8-111">Handles opened by the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) are closed, and memory allocated for the handle and string arrays is freed.</span></span>  
  
 <span data-ttu-id="7b7e8-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="7b7e8-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="7b7e8-113">Délka `pHandleArray` neodpovídá délka, který se předává v `dwArrayLength`.</span><span class="sxs-lookup"><span data-stu-id="7b7e8-113">The length of `pHandleArray` does not match the length that is passed in `dwArrayLength`.</span></span>  
  
 <span data-ttu-id="7b7e8-114">E_FAIL (nebo ostatní návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="7b7e8-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="7b7e8-115">Funkce nelze uvolnit paměť pro `pHandleArray` a `pStringArray`.</span><span class="sxs-lookup"><span data-stu-id="7b7e8-115">The function is unable to free the memory for `pHandleArray` and `pStringArray`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b7e8-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7b7e8-116">Requirements</span></span>  
 <span data-ttu-id="7b7e8-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b7e8-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b7e8-118">**Záhlaví:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="7b7e8-118">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="7b7e8-119">**Knihovna:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="7b7e8-119">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="7b7e8-120">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="7b7e8-120">**.NET Framework Versions:** 3.5 SP1</span></span>
