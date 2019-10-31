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
ms.openlocfilehash: 3611684a17d51fc4fdba31dd4049540039b43e8b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73110518"
---
# <a name="icordebugappdomainenumeratebreakpoints-method"></a><span data-ttu-id="937de-102">ICorDebugAppDomain::EnumerateBreakpoints – metoda</span><span class="sxs-lookup"><span data-stu-id="937de-102">ICorDebugAppDomain::EnumerateBreakpoints Method</span></span>
<span data-ttu-id="937de-103">Získá enumerátor pro všechny aktivní zarážky v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="937de-103">Gets an enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="937de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="937de-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateBreakpoints (  
    [out] ICorDebugBreakpointEnum   **ppBreakpoints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="937de-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="937de-105">Parameters</span></span>  
 `ppBreakpoints`  
 <span data-ttu-id="937de-106">mimo Ukazatel na adresu objektu ICorDebugBreakpointEnum, který je enumerátorem všech aktivních zarážek v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="937de-106">[out] A pointer to the address of an ICorDebugBreakpointEnum object that is the enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="937de-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="937de-107">Remarks</span></span>  
 <span data-ttu-id="937de-108">Enumerátor zahrnuje všechny typy zarážek, včetně zarážek funkcí a datových zarážek.</span><span class="sxs-lookup"><span data-stu-id="937de-108">The enumerator includes all types of breakpoints, including function breakpoints and data breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="937de-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="937de-109">Requirements</span></span>  
 <span data-ttu-id="937de-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="937de-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="937de-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="937de-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="937de-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="937de-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="937de-113">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="937de-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
