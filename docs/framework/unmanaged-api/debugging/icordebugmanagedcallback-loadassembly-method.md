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
ms.openlocfilehash: f1d05914004d3c1fcc5ff109e854d01661367835
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413115"
---
# <a name="icordebugmanagedcallbackloadassembly-method"></a><span data-ttu-id="ffc6f-102">ICorDebugManagedCallback::LoadAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="ffc6f-102">ICorDebugManagedCallback::LoadAssembly Method</span></span>
<span data-ttu-id="ffc6f-103">Běžné sestavení modulu runtime (CLR) jazyk byl úspěšně načíst upozorní ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="ffc6f-103">Notifies the debugger that a common language runtime (CLR) assembly has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffc6f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ffc6f-104">Syntax</span></span>  
  
```  
HRESULT LoadAssembly (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugAssembly  *pAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ffc6f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ffc6f-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="ffc6f-106">[v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace, do kterého má sestavení bylo načteno.</span><span class="sxs-lookup"><span data-stu-id="ffc6f-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the assembly has been loaded.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="ffc6f-107">[v] Ukazatel na ICorDebugAssembly objekt, který představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="ffc6f-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffc6f-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ffc6f-108">Requirements</span></span>  
 <span data-ttu-id="ffc6f-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffc6f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffc6f-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ffc6f-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ffc6f-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ffc6f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ffc6f-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffc6f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffc6f-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="ffc6f-113">See Also</span></span>  
 [<span data-ttu-id="ffc6f-114">UnloadAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="ffc6f-114">UnloadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadassembly-method.md)  
 [<span data-ttu-id="ffc6f-115">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ffc6f-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
