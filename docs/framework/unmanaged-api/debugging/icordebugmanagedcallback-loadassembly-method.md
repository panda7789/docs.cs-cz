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
ms.openlocfilehash: 8cb8699c103f48b42694449a2bb2bbd25c42d3c6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212724"
---
# <a name="icordebugmanagedcallbackloadassembly-method"></a><span data-ttu-id="dee33-102">ICorDebugManagedCallback::LoadAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="dee33-102">ICorDebugManagedCallback::LoadAssembly Method</span></span>
<span data-ttu-id="dee33-103">Oznamuje ladicímu programu, že bylo úspěšně načteno sestavení modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="dee33-103">Notifies the debugger that a common language runtime (CLR) assembly has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dee33-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dee33-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadAssembly (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugAssembly  *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dee33-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dee33-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="dee33-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, do které bylo sestavení načteno.</span><span class="sxs-lookup"><span data-stu-id="dee33-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the assembly has been loaded.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="dee33-107">pro Ukazatel na objekt ICorDebugAssembly, který představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="dee33-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dee33-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dee33-108">Requirements</span></span>  
 <span data-ttu-id="dee33-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dee33-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dee33-110">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dee33-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dee33-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="dee33-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dee33-112">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dee33-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dee33-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="dee33-113">See also</span></span>

- [<span data-ttu-id="dee33-114">UnloadAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="dee33-114">UnloadAssembly Method</span></span>](icordebugmanagedcallback-unloadassembly-method.md)
- [<span data-ttu-id="dee33-115">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dee33-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
