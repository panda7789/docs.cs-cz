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
ms.openlocfilehash: 80836cbbf82a97ccd6dc7251e5cbe934e0cbe66f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777280"
---
# <a name="icordebugmanagedcallbackloadassembly-method"></a><span data-ttu-id="d4cb1-102">ICorDebugManagedCallback::LoadAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="d4cb1-102">ICorDebugManagedCallback::LoadAssembly Method</span></span>
<span data-ttu-id="d4cb1-103">Oznamuje ladicímu programu, že bylo úspěšně načteno sestavení modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="d4cb1-103">Notifies the debugger that a common language runtime (CLR) assembly has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4cb1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4cb1-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadAssembly (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugAssembly  *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4cb1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d4cb1-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="d4cb1-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, do které bylo sestavení načteno.</span><span class="sxs-lookup"><span data-stu-id="d4cb1-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the assembly has been loaded.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="d4cb1-107">pro Ukazatel na objekt ICorDebugAssembly, který představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="d4cb1-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4cb1-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d4cb1-108">Requirements</span></span>  
 <span data-ttu-id="d4cb1-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4cb1-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4cb1-110">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d4cb1-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4cb1-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d4cb1-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4cb1-112">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4cb1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4cb1-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d4cb1-113">See also</span></span>

- [<span data-ttu-id="d4cb1-114">UnloadAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="d4cb1-114">UnloadAssembly Method</span></span>](icordebugmanagedcallback-unloadassembly-method.md)
- [<span data-ttu-id="d4cb1-115">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d4cb1-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
