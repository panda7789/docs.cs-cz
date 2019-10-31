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
ms.openlocfilehash: d13c5be314dc39f3e7b42a8d6b13f6a25751067d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130717"
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a><span data-ttu-id="d5fd0-102">ICorDebugManagedCallback::LoadModule – metoda</span><span class="sxs-lookup"><span data-stu-id="d5fd0-102">ICorDebugManagedCallback::LoadModule Method</span></span>
<span data-ttu-id="d5fd0-103">Oznamuje ladicímu programu, že modul CLR (Common Language Runtime) byl úspěšně načten.</span><span class="sxs-lookup"><span data-stu-id="d5fd0-103">Notifies the debugger that a common language runtime (CLR) module has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5fd0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5fd0-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5fd0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d5fd0-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="d5fd0-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, do které byl modul načten.</span><span class="sxs-lookup"><span data-stu-id="d5fd0-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the module has been loaded.</span></span>  
  
 `pModule`  
 <span data-ttu-id="d5fd0-107">pro Ukazatel na objekt ICorDebugModule, který představuje modul CLR.</span><span class="sxs-lookup"><span data-stu-id="d5fd0-107">[in] A pointer to an ICorDebugModule object that represents the CLR module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5fd0-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d5fd0-108">Remarks</span></span>  
 <span data-ttu-id="d5fd0-109">`LoadModule` zpětné volání poskytuje vhodný čas pro prověření metadat pro modul, nastavení příznaků kompilátoru JIT (just-in-time) nebo povolení nebo zakázání zpětného volání pro načítání tříd pro modul.</span><span class="sxs-lookup"><span data-stu-id="d5fd0-109">The `LoadModule` callback provides an appropriate time to examine metadata for the module, set just-in-time (JIT) compiler flags, or enable or disable class loading callbacks for the module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5fd0-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d5fd0-110">Requirements</span></span>  
 <span data-ttu-id="d5fd0-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5fd0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5fd0-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d5fd0-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5fd0-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d5fd0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5fd0-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5fd0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5fd0-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d5fd0-115">See also</span></span>

- [<span data-ttu-id="d5fd0-116">UnloadModule – metoda</span><span class="sxs-lookup"><span data-stu-id="d5fd0-116">UnloadModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)
- [<span data-ttu-id="d5fd0-117">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5fd0-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
