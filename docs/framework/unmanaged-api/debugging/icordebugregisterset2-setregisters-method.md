---
title: ICorDebugRegisterSet2::SetRegisters – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.SetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::SetRegisters
helpviewer_keywords:
- ICorDebugRegisterSet2::SetRegisters method [.NET Framework debugging]
- SetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: fe0ac7e7-c9e1-4ec1-9f4e-1c56d63d73ac
topic_type:
- apiref
ms.openlocfilehash: ebbd8dc2b715541850ed3b3bc530c0dd28993e1d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378131"
---
# <a name="icordebugregisterset2setregisters-method"></a><span data-ttu-id="f19ac-102">ICorDebugRegisterSet2::SetRegisters – metoda</span><span class="sxs-lookup"><span data-stu-id="f19ac-102">ICorDebugRegisterSet2::SetRegisters Method</span></span>
<span data-ttu-id="f19ac-103">`SetRegisters`není implementována v .NET Framework verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="f19ac-103">`SetRegisters` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="f19ac-104">Nevolejte tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="f19ac-104">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f19ac-105">Použijte operace vyšší úrovně, například [ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md) nebo [ICorDebugNativeFrame:: SetIP](icordebugnativeframe-setip-method.md).</span><span class="sxs-lookup"><span data-stu-id="f19ac-105">Use the higher-level operations such as [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) or [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f19ac-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f19ac-106">Syntax</span></span>  
  
```cpp  
HRESULT SetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="f19ac-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f19ac-107">Requirements</span></span>  
 <span data-ttu-id="f19ac-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f19ac-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f19ac-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f19ac-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f19ac-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f19ac-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f19ac-111">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f19ac-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f19ac-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="f19ac-112">See also</span></span>

- [<span data-ttu-id="f19ac-113">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f19ac-113">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
- [<span data-ttu-id="f19ac-114">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f19ac-114">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
