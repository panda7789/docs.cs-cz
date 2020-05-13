---
title: ICorDebugManagedCallback::UnloadModule – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadModule
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadModule method [.NET Framework debugging]
- UnloadModule method [.NET Framework debugging]
ms.assetid: b12bfcd9-1e29-48bf-9a3d-44bfae5df5e8
topic_type:
- apiref
ms.openlocfilehash: 4b44a16d143c1daea1ea6c36eb096ab9a937b272
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210039"
---
# <a name="icordebugmanagedcallbackunloadmodule-method"></a><span data-ttu-id="cd09d-102">ICorDebugManagedCallback::UnloadModule – metoda</span><span class="sxs-lookup"><span data-stu-id="cd09d-102">ICorDebugManagedCallback::UnloadModule Method</span></span>
<span data-ttu-id="cd09d-103">Oznamuje ladicímu programu, že byl uvolněn modul common language runtime (DLL).</span><span class="sxs-lookup"><span data-stu-id="cd09d-103">Notifies the debugger that a common language runtime module (DLL) has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd09d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd09d-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadModule (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugModule     *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd09d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cd09d-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="cd09d-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje aplikační doménu, která obsahuje modul.</span><span class="sxs-lookup"><span data-stu-id="cd09d-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the module.</span></span>  
  
 `pModule`  
 <span data-ttu-id="cd09d-107">pro Ukazatel na objekt ICorDebugModule, který představuje modul.</span><span class="sxs-lookup"><span data-stu-id="cd09d-107">[in] A pointer to an ICorDebugModule object that represents the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd09d-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cd09d-108">Remarks</span></span>  
 <span data-ttu-id="cd09d-109">Modul by neměl být použit po tomto volání.</span><span class="sxs-lookup"><span data-stu-id="cd09d-109">The module should not be used after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd09d-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cd09d-110">Requirements</span></span>  
 <span data-ttu-id="cd09d-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd09d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd09d-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cd09d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cd09d-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cd09d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd09d-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd09d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd09d-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd09d-115">See also</span></span>

- [<span data-ttu-id="cd09d-116">LoadModule – metoda</span><span class="sxs-lookup"><span data-stu-id="cd09d-116">LoadModule Method</span></span>](icordebugmanagedcallback-loadmodule-method.md)
- [<span data-ttu-id="cd09d-117">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cd09d-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
