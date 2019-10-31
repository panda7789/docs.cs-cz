---
title: ICorDebugAppDomain::Attach – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.Attach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::Attach
helpviewer_keywords:
- ICorDebugAppDomain::Attach method [.NET Framework debugging]
- Attach method [.NET Framework debugging]
ms.assetid: 0358b84a-4236-4c34-945b-4babff7df570
topic_type:
- apiref
ms.openlocfilehash: 66ec64b1a855a3d31f14f3ef29dde0b82361f5d7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133986"
---
# <a name="icordebugappdomainattach-method"></a><span data-ttu-id="7fd0d-102">ICorDebugAppDomain::Attach – metoda</span><span class="sxs-lookup"><span data-stu-id="7fd0d-102">ICorDebugAppDomain::Attach Method</span></span>
<span data-ttu-id="7fd0d-103">Připojí ladicí program k doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="7fd0d-103">Attaches the debugger to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fd0d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7fd0d-104">Syntax</span></span>  
  
```cpp  
HRESULT Attach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="7fd0d-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7fd0d-105">Remarks</span></span>  
 <span data-ttu-id="7fd0d-106">Aby bylo možné přijímat události a povolit ladění aplikační domény, musí být ladicí program připojen k doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="7fd0d-106">The debugger must be attached to the application domain to receive events and to enable debugging of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fd0d-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7fd0d-107">Requirements</span></span>  
 <span data-ttu-id="7fd0d-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fd0d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fd0d-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7fd0d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7fd0d-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7fd0d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7fd0d-111">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fd0d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
