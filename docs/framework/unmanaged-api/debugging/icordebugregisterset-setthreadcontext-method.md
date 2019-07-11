---
title: ICorDebugRegisterSet::SetThreadContext – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::SetThreadContext
helpviewer_keywords:
- ICorDebugRegisterSet::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 73afa930-32cb-4c40-81f8-83e8e6fbe213
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: debb704900d852df1d66c7bac65ab385e0d72ec5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769940"
---
# <a name="icordebugregistersetsetthreadcontext-method"></a><span data-ttu-id="13115-102">ICorDebugRegisterSet::SetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="13115-102">ICorDebugRegisterSet::SetThreadContext Method</span></span>
<span data-ttu-id="13115-103">`SetThreadContext` není implementováno v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="13115-103">`SetThreadContext` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="13115-104">Nevolejte tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="13115-104">Do not call this method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="13115-105">Pomocí operace vyšší úrovně [icordebugnativeframe::setip –](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) k nastavení kontextu vlákna.</span><span class="sxs-lookup"><span data-stu-id="13115-105">Use the higher-level operation [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) to set the context of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13115-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13115-106">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize),  
         size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="13115-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="13115-107">Requirements</span></span>  
 <span data-ttu-id="13115-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13115-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13115-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="13115-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="13115-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13115-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13115-111">**Verze rozhraní .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="13115-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13115-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="13115-112">See also</span></span>

- [<span data-ttu-id="13115-113">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="13115-113">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="13115-114">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="13115-114">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
