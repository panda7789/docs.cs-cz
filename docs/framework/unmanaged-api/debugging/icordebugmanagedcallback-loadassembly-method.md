---
title: ICorDebugManagedCallback::LoadAssembly – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadAssembly
helpviewer_keywords:
- LoadAssembly method [.NET Framework debugging]
- ICorDebugManagedCallback::LoadAssembly method [.NET Framework debugging]
ms.assetid: 55cb673a-e240-43a6-a406-6912e7c0fe66
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5760287e01257e3f0fc99a18ba20f2f2a1b2b3af
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083358"
---
# <a name="icordebugmanagedcallbackloadassembly-method"></a><span data-ttu-id="2e8f2-102">ICorDebugManagedCallback::LoadAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="2e8f2-102">ICorDebugManagedCallback::LoadAssembly Method</span></span>
<span data-ttu-id="2e8f2-103">Upozorní ladicího programu, že sestavení common language runtime (CLR) byl úspěšně načten.</span><span class="sxs-lookup"><span data-stu-id="2e8f2-103">Notifies the debugger that a common language runtime (CLR) assembly has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e8f2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e8f2-104">Syntax</span></span>  
  
```  
HRESULT LoadAssembly (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugAssembly  *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e8f2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2e8f2-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="2e8f2-106">[in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, do které sestavení bylo načteno.</span><span class="sxs-lookup"><span data-stu-id="2e8f2-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the assembly has been loaded.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="2e8f2-107">[in] Ukazatel na objekt icordebugassembly –, který představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="2e8f2-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e8f2-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2e8f2-108">Requirements</span></span>  
 <span data-ttu-id="2e8f2-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e8f2-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e8f2-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2e8f2-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e8f2-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e8f2-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e8f2-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e8f2-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e8f2-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2e8f2-113">See also</span></span>

- [<span data-ttu-id="2e8f2-114">UnloadAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="2e8f2-114">UnloadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadassembly-method.md)
- [<span data-ttu-id="2e8f2-115">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e8f2-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
