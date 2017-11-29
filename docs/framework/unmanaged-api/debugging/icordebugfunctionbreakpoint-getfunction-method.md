---
title: "ICorDebugFunctionBreakpoint::GetFunction – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunctionBreakpoint.GetFunction
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunctionBreakpoint::GetFunction
helpviewer_keywords:
- ICorDebugFunctionBreakpoint::GetFunction method [.NET Framework debugging]
- GetFunction method, ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: 2a62dae5-dd8a-4696-b817-0e1e586c24a0
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 853a7989c98db3160b46a5d897cb83e64ca355e0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunctionbreakpointgetfunction-method"></a><span data-ttu-id="5fe8b-102">ICorDebugFunctionBreakpoint::GetFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="5fe8b-102">ICorDebugFunctionBreakpoint::GetFunction Method</span></span>
<span data-ttu-id="5fe8b-103">Získá ukazatele rozhraní umožňuje ICorDebugFunction, který odkazuje na funkci, ve kterém je nastaven breakpoint.</span><span class="sxs-lookup"><span data-stu-id="5fe8b-103">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fe8b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5fe8b-104">Syntax</span></span>  
  
```  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5fe8b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5fe8b-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="5fe8b-106">[out] Ukazatel na adresu funkce, ve kterém je nastaven breakpoint.</span><span class="sxs-lookup"><span data-stu-id="5fe8b-106">[out] A pointer to the address of the function in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fe8b-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5fe8b-107">Requirements</span></span>  
 <span data-ttu-id="5fe8b-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fe8b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fe8b-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5fe8b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5fe8b-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5fe8b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5fe8b-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fe8b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
