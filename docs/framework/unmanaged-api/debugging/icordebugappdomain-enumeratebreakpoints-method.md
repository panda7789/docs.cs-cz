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
ms.openlocfilehash: bb994ae32c9e0e61c06c60521361a5c6c78d12fa
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895281"
---
# <a name="icordebugappdomainenumeratebreakpoints-method"></a><span data-ttu-id="2645f-102">ICorDebugAppDomain::EnumerateBreakpoints – metoda</span><span class="sxs-lookup"><span data-stu-id="2645f-102">ICorDebugAppDomain::EnumerateBreakpoints Method</span></span>
<span data-ttu-id="2645f-103">Získá enumerátor pro všechny aktivní zarážky v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="2645f-103">Gets an enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2645f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2645f-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateBreakpoints (  
    [out] ICorDebugBreakpointEnum   **ppBreakpoints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2645f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2645f-105">Parameters</span></span>  
 `ppBreakpoints`  
 <span data-ttu-id="2645f-106">mimo Ukazatel na adresu objektu ICorDebugBreakpointEnum, který je enumerátorem všech aktivních zarážek v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="2645f-106">[out] A pointer to the address of an ICorDebugBreakpointEnum object that is the enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2645f-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2645f-107">Remarks</span></span>  
 <span data-ttu-id="2645f-108">Enumerátor zahrnuje všechny typy zarážek, včetně zarážek funkcí a datových zarážek.</span><span class="sxs-lookup"><span data-stu-id="2645f-108">The enumerator includes all types of breakpoints, including function breakpoints and data breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2645f-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2645f-109">Requirements</span></span>  
 <span data-ttu-id="2645f-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2645f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2645f-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2645f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2645f-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2645f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2645f-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2645f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
