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
ms.openlocfilehash: cd4a16bc8b48f147ed03555b51eee5f42a445bc6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212696"
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a><span data-ttu-id="401a9-102">ICorDebugManagedCallback::LoadModule – metoda</span><span class="sxs-lookup"><span data-stu-id="401a9-102">ICorDebugManagedCallback::LoadModule Method</span></span>
<span data-ttu-id="401a9-103">Oznamuje ladicímu programu, že modul CLR (Common Language Runtime) byl úspěšně načten.</span><span class="sxs-lookup"><span data-stu-id="401a9-103">Notifies the debugger that a common language runtime (CLR) module has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="401a9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="401a9-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="401a9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="401a9-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="401a9-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, do které byl modul načten.</span><span class="sxs-lookup"><span data-stu-id="401a9-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the module has been loaded.</span></span>  
  
 `pModule`  
 <span data-ttu-id="401a9-107">pro Ukazatel na objekt ICorDebugModule, který představuje modul CLR.</span><span class="sxs-lookup"><span data-stu-id="401a9-107">[in] A pointer to an ICorDebugModule object that represents the CLR module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="401a9-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="401a9-108">Remarks</span></span>  
 <span data-ttu-id="401a9-109">`LoadModule`Zpětné volání poskytuje vhodný čas pro prověření metadat pro modul, nastavování příznaků kompilátoru JIT (just-in-time) nebo povolení nebo zakázání zpětného volání pro načítání tříd pro modul.</span><span class="sxs-lookup"><span data-stu-id="401a9-109">The `LoadModule` callback provides an appropriate time to examine metadata for the module, set just-in-time (JIT) compiler flags, or enable or disable class loading callbacks for the module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="401a9-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="401a9-110">Requirements</span></span>  
 <span data-ttu-id="401a9-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="401a9-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="401a9-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="401a9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="401a9-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="401a9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="401a9-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="401a9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="401a9-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="401a9-115">See also</span></span>

- [<span data-ttu-id="401a9-116">UnloadModule – metoda</span><span class="sxs-lookup"><span data-stu-id="401a9-116">UnloadModule Method</span></span>](icordebugmanagedcallback-unloadmodule-method.md)
- [<span data-ttu-id="401a9-117">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="401a9-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
