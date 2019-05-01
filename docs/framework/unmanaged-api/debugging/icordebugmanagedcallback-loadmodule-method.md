---
title: ICorDebugManagedCallback::LoadModule – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadModule
helpviewer_keywords:
- ICorDebugManagedCallback::LoadModule method [.NET Framework debugging]
- LoadModule method [.NET Framework debugging]
ms.assetid: 66ec04e9-87cb-42ce-9720-81522abb5d5a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cfca06c656f3274f4c5ddb06373a0296dc5e6905
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995186"
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a><span data-ttu-id="18025-102">ICorDebugManagedCallback::LoadModule – metoda</span><span class="sxs-lookup"><span data-stu-id="18025-102">ICorDebugManagedCallback::LoadModule Method</span></span>
<span data-ttu-id="18025-103">Upozorní ladicí program úspěšně načtena společného jazykového modulu runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="18025-103">Notifies the debugger that a common language runtime (CLR) module has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18025-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18025-104">Syntax</span></span>  
  
```  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18025-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="18025-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="18025-106">[in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, do kterého byl modul načten.</span><span class="sxs-lookup"><span data-stu-id="18025-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the module has been loaded.</span></span>  
  
 `pModule`  
 <span data-ttu-id="18025-107">[in] Ukazatel na objekt icordebugmodule –, který představuje modul CLR.</span><span class="sxs-lookup"><span data-stu-id="18025-107">[in] A pointer to an ICorDebugModule object that represents the CLR module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18025-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="18025-108">Remarks</span></span>  
 <span data-ttu-id="18025-109">`LoadModule` Zpětného volání obsahuje příslušný čas přezkoumání metadat pro modul, nastavit příznaky kompilátoru just-in-time (JIT), nebo povolit nebo zakázat třídu načítající zpětná volání pro modul.</span><span class="sxs-lookup"><span data-stu-id="18025-109">The `LoadModule` callback provides an appropriate time to examine metadata for the module, set just-in-time (JIT) compiler flags, or enable or disable class loading callbacks for the module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18025-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="18025-110">Requirements</span></span>  
 <span data-ttu-id="18025-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18025-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18025-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="18025-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="18025-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="18025-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18025-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18025-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18025-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="18025-115">See also</span></span>

- [<span data-ttu-id="18025-116">UnloadModule – metoda</span><span class="sxs-lookup"><span data-stu-id="18025-116">UnloadModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)
- [<span data-ttu-id="18025-117">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18025-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
