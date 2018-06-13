---
title: ICorDebugManagedCallback::Break – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Break
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Break
helpviewer_keywords:
- Break method [.NET Framework debugging]
- ICorDebugManagedCallback::Break method [.NET Framework debugging]
ms.assetid: 7d78a301-82b3-43b2-9d65-3cda3285ae97
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d7120e092b422b755ecbde9e48236b42e67636fc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414935"
---
# <a name="icordebugmanagedcallbackbreak-method"></a><span data-ttu-id="33c30-102">ICorDebugManagedCallback::Break – metoda</span><span class="sxs-lookup"><span data-stu-id="33c30-102">ICorDebugManagedCallback::Break Method</span></span>
<span data-ttu-id="33c30-103">Upozorní ladicího programu při <xref:System.Reflection.Emit.OpCodes.Break> provedení instrukcí v datovém proudu kódu.</span><span class="sxs-lookup"><span data-stu-id="33c30-103">Notifies the debugger when a <xref:System.Reflection.Emit.OpCodes.Break> instruction in the code stream is executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33c30-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33c30-104">Syntax</span></span>  
  
```  
HRESULT Break (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="33c30-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="33c30-105">Parameters</span></span>  
 `pAppDOmain`  
 <span data-ttu-id="33c30-106">[v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace, která obsahuje pokyn přerušení.</span><span class="sxs-lookup"><span data-stu-id="33c30-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the break instruction.</span></span>  
  
 `thread`  
 <span data-ttu-id="33c30-107">[v] Ukazatel na ICorDebugThread objekt, který reprezentuje podproces, který obsahuje instrukce přerušení.</span><span class="sxs-lookup"><span data-stu-id="33c30-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the break instruction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33c30-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="33c30-108">Requirements</span></span>  
 <span data-ttu-id="33c30-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33c30-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33c30-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="33c30-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33c30-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33c30-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33c30-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33c30-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33c30-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="33c30-113">See Also</span></span>  
 [<span data-ttu-id="33c30-114">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="33c30-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
