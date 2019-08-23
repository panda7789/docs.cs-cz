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
ms.openlocfilehash: ff1365ddb46ca28cbcaa4f1383b293681e6ec214
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956774"
---
# <a name="icordebugregistersetsetthreadcontext-method"></a><span data-ttu-id="58558-102">ICorDebugRegisterSet::SetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="58558-102">ICorDebugRegisterSet::SetThreadContext Method</span></span>
<span data-ttu-id="58558-103">`SetThreadContext`není implementována v .NET Framework verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="58558-103">`SetThreadContext` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="58558-104">Nevolejte tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="58558-104">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="58558-105">Pro nastavení kontextu vlákna použijte operaci vyšší úrovně [ICorDebugNativeFrame:: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) .</span><span class="sxs-lookup"><span data-stu-id="58558-105">Use the higher-level operation [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) to set the context of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58558-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58558-106">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize),  
         size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="58558-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="58558-107">Requirements</span></span>  
 <span data-ttu-id="58558-108">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58558-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58558-109">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="58558-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58558-110">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58558-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58558-111">**Verze .NET Framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="58558-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58558-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="58558-112">See also</span></span>

- [<span data-ttu-id="58558-113">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="58558-113">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="58558-114">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="58558-114">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
