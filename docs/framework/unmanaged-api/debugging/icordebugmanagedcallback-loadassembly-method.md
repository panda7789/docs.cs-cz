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
ms.openlocfilehash: c6d77ff1393bc0ba4884dfa34810fee5316e33ef
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130745"
---
# <a name="icordebugmanagedcallbackloadassembly-method"></a><span data-ttu-id="f3507-102">ICorDebugManagedCallback::LoadAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="f3507-102">ICorDebugManagedCallback::LoadAssembly Method</span></span>
<span data-ttu-id="f3507-103">Oznamuje ladicímu programu, že bylo úspěšně načteno sestavení modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="f3507-103">Notifies the debugger that a common language runtime (CLR) assembly has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3507-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3507-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadAssembly (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugAssembly  *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3507-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f3507-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="f3507-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, do které bylo sestavení načteno.</span><span class="sxs-lookup"><span data-stu-id="f3507-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the assembly has been loaded.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="f3507-107">pro Ukazatel na objekt ICorDebugAssembly, který představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="f3507-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3507-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f3507-108">Requirements</span></span>  
 <span data-ttu-id="f3507-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3507-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3507-110">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f3507-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f3507-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f3507-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3507-112">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3507-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3507-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f3507-113">See also</span></span>

- [<span data-ttu-id="f3507-114">UnloadAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="f3507-114">UnloadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadassembly-method.md)
- [<span data-ttu-id="f3507-115">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f3507-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
