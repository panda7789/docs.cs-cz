---
title: ICorDebugAppDomain::EnumerateBreakpoints – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.EnumerateBreakpoints
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateBreakpoints
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateBreakpoints method [.NET Framework debugging]
- EnumerateBreakpoints method [.NET Framework debugging]
ms.assetid: 206069c5-25cb-4794-9d69-67c5aa7ed0af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b00afc900a27aea94389ee81065ea22ae359440d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996265"
---
# <a name="icordebugappdomainenumeratebreakpoints-method"></a><span data-ttu-id="a29ee-102">ICorDebugAppDomain::EnumerateBreakpoints – metoda</span><span class="sxs-lookup"><span data-stu-id="a29ee-102">ICorDebugAppDomain::EnumerateBreakpoints Method</span></span>
<span data-ttu-id="a29ee-103">Získá enumerátor pro všechny zarážky aktivní v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="a29ee-103">Gets an enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a29ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a29ee-104">Syntax</span></span>  
  
```  
HRESULT EnumerateBreakpoints (  
    [out] ICorDebugBreakpointEnum   **ppBreakpoints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a29ee-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a29ee-105">Parameters</span></span>  
 `ppBreakpoints`  
 <span data-ttu-id="a29ee-106">[out] Ukazatel na adresu icordebugbreakpointenum – objekt, který je výčet všech aktivních zarážek v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="a29ee-106">[out] A pointer to the address of an ICorDebugBreakpointEnum object that is the enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a29ee-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a29ee-107">Remarks</span></span>  
 <span data-ttu-id="a29ee-108">Enumerátor zahrnují všechny typy zarážky, včetně zarážky funkcí a datové zarážky.</span><span class="sxs-lookup"><span data-stu-id="a29ee-108">The enumerator includes all types of breakpoints, including function breakpoints and data breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a29ee-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a29ee-109">Requirements</span></span>  
 <span data-ttu-id="a29ee-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a29ee-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a29ee-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a29ee-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a29ee-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a29ee-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a29ee-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a29ee-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
