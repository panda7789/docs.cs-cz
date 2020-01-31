---
title: ICorDebugManagedCallback::UnloadAssembly – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadAssembly
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadAssembly method [.NET Framework debugging]
- UnloadAssembly method [.NET Framework debugging]
ms.assetid: 6734321c-c8a9-401f-a558-cad715ec4a77
topic_type:
- apiref
ms.openlocfilehash: 06c08499298656c8314d72667d9dac88c8d11e6a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788346"
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="9395d-102">ICorDebugManagedCallback::UnloadAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="9395d-102">ICorDebugManagedCallback::UnloadAssembly Method</span></span>
<span data-ttu-id="9395d-103">Oznamuje ladicímu programu, že bylo uvolněno sestavení společného jazykového modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="9395d-103">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9395d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9395d-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9395d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9395d-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="9395d-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje aplikační doménu, která obsahuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="9395d-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="9395d-107">pro Ukazatel na objekt ICorDebugAssembly, který představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="9395d-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9395d-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9395d-108">Remarks</span></span>  
 <span data-ttu-id="9395d-109">Po tomto zpětném volání by se nemělo používat sestavení.</span><span class="sxs-lookup"><span data-stu-id="9395d-109">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9395d-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9395d-110">Requirements</span></span>  
 <span data-ttu-id="9395d-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9395d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9395d-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9395d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9395d-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9395d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9395d-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9395d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9395d-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9395d-115">See also</span></span>

- [<span data-ttu-id="9395d-116">LoadAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="9395d-116">LoadAssembly Method</span></span>](icordebugmanagedcallback-loadassembly-method.md)
- [<span data-ttu-id="9395d-117">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9395d-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
