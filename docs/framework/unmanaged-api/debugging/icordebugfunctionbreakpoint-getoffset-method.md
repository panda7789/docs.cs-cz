---
title: ICorDebugFunctionBreakpoint::GetOffset – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunctionBreakpoint.GetOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunctionBreakpoint::GetOffset
helpviewer_keywords:
- ICorDebugFunctionBreakpoint::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: e619eae4-3ac3-4c37-bba4-55e59989b9cb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6253191340c2f2d4f42f47d580b9d923ab3ff041
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651685"
---
# <a name="icordebugfunctionbreakpointgetoffset-method"></a><span data-ttu-id="dc14a-102">ICorDebugFunctionBreakpoint::GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="dc14a-102">ICorDebugFunctionBreakpoint::GetOffset Method</span></span>
<span data-ttu-id="dc14a-103">Získá posun zarážku v rámci této funkce.</span><span class="sxs-lookup"><span data-stu-id="dc14a-103">Gets the offset of the breakpoint within the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc14a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc14a-104">Syntax</span></span>  
  
```  
HRESULT GetOffset (  
    [out] ULONG32  *pnOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc14a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dc14a-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="dc14a-106">[out] Ukazatel na posun zarážku.</span><span class="sxs-lookup"><span data-stu-id="dc14a-106">[out] A pointer to the offset of the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc14a-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dc14a-107">Requirements</span></span>  
 <span data-ttu-id="dc14a-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc14a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc14a-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dc14a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc14a-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc14a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc14a-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc14a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
