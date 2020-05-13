---
title: ICorDebugRegisterSet::SetRegisters – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.SetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::SetRegisters
helpviewer_keywords:
- SetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::SetRegisters method [.NET Framework debugging]
ms.assetid: ac6244b9-54ba-475f-b72a-abed6afc46ec
topic_type:
- apiref
ms.openlocfilehash: eba86c09197aad6bac284c52fe164432e197c6f7
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378251"
---
# <a name="icordebugregistersetsetregisters-method"></a><span data-ttu-id="be943-102">ICorDebugRegisterSet::SetRegisters – metoda</span><span class="sxs-lookup"><span data-stu-id="be943-102">ICorDebugRegisterSet::SetRegisters Method</span></span>
<span data-ttu-id="be943-103">`SetRegisters`není implementována v .NET Framework verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="be943-103">`SetRegisters` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="be943-104">Nevolejte tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="be943-104">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="be943-105">Použijte operace vyšší úrovně, například [ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md) nebo [ICorDebugNativeFrame:: SetIP](icordebugnativeframe-setip-method.md).</span><span class="sxs-lookup"><span data-stu-id="be943-105">Use the higher-level operations such as [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) or [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be943-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be943-106">Syntax</span></span>  
  
```cpp  
HRESULT SetRegisters (  
    [in] ULONG64   mask,  
    [in] ULONG32   regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="be943-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="be943-107">Requirements</span></span>  
 <span data-ttu-id="be943-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be943-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be943-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="be943-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be943-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="be943-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be943-111">**Verze .NET Framework:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="be943-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be943-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="be943-112">See also</span></span>

- [<span data-ttu-id="be943-113">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="be943-113">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="be943-114">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="be943-114">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
