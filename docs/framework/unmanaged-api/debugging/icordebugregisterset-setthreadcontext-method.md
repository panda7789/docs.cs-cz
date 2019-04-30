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
ms.openlocfilehash: 7b1ea34c187de99d23b05b5e1a30c53bc54a6c0c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782795"
---
# <a name="icordebugregistersetsetthreadcontext-method"></a><span data-ttu-id="1a0cd-102">ICorDebugRegisterSet::SetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="1a0cd-102">ICorDebugRegisterSet::SetThreadContext Method</span></span>
<span data-ttu-id="1a0cd-103">`SetThreadContext` není implementováno v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="1a0cd-103">`SetThreadContext` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="1a0cd-104">Nevolejte tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="1a0cd-104">Do not call this method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1a0cd-105">Pomocí operace vyšší úrovně [icordebugnativeframe::setip –](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) k nastavení kontextu vlákna.</span><span class="sxs-lookup"><span data-stu-id="1a0cd-105">Use the higher-level operation [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) to set the context of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a0cd-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a0cd-106">Syntax</span></span>  
  
```  
HRESULT SetThreadContext (  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize),  
         size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="1a0cd-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1a0cd-107">Requirements</span></span>  
 <span data-ttu-id="1a0cd-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a0cd-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a0cd-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1a0cd-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a0cd-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a0cd-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a0cd-111">**Verze rozhraní .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="1a0cd-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a0cd-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1a0cd-112">See also</span></span>

- [<span data-ttu-id="1a0cd-113">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1a0cd-113">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="1a0cd-114">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1a0cd-114">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
