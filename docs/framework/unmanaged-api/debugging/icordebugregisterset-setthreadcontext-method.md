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
ms.openlocfilehash: dc2a41524d3fafe1cb45c9494d80aabe7dae0ed8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792031"
---
# <a name="icordebugregistersetsetthreadcontext-method"></a><span data-ttu-id="8850b-102">ICorDebugRegisterSet::SetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="8850b-102">ICorDebugRegisterSet::SetThreadContext Method</span></span>
<span data-ttu-id="8850b-103">`SetThreadContext` není implementována v .NET Framework verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="8850b-103">`SetThreadContext` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="8850b-104">Nevolejte tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="8850b-104">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8850b-105">Pro nastavení kontextu vlákna použijte operaci vyšší úrovně [ICorDebugNativeFrame:: SetIP](icordebugnativeframe-setip-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8850b-105">Use the higher-level operation [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md) to set the context of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8850b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8850b-106">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize),  
         size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="8850b-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8850b-107">Requirements</span></span>  
 <span data-ttu-id="8850b-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8850b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8850b-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8850b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8850b-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8850b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8850b-111">**Verze .NET Framework:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="8850b-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8850b-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8850b-112">See also</span></span>

- [<span data-ttu-id="8850b-113">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8850b-113">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="8850b-114">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8850b-114">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
