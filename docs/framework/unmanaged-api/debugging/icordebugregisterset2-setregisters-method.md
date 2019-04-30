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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4cd4f7e1b0737672f33bdd7fec4f7953e20593f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782808"
---
# <a name="icordebugregisterset2setregisters-method"></a><span data-ttu-id="2cc99-102">ICorDebugRegisterSet2::SetRegisters – metoda</span><span class="sxs-lookup"><span data-stu-id="2cc99-102">ICorDebugRegisterSet2::SetRegisters Method</span></span>
<span data-ttu-id="2cc99-103">`SetRegisters` není implementováno v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="2cc99-103">`SetRegisters` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="2cc99-104">Nevolejte tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="2cc99-104">Do not call this method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2cc99-105">Pomocí operace vyšší úrovně, jako [icordebugilframe::setip –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) nebo [icordebugnativeframe::setip –](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md).</span><span class="sxs-lookup"><span data-stu-id="2cc99-105">Use the higher-level operations such as [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) or [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cc99-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2cc99-106">Syntax</span></span>  
  
```  
HRESULT SetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="2cc99-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2cc99-107">Requirements</span></span>  
 <span data-ttu-id="2cc99-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cc99-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cc99-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2cc99-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2cc99-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2cc99-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2cc99-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cc99-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cc99-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2cc99-112">See also</span></span>

- [<span data-ttu-id="2cc99-113">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2cc99-113">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [<span data-ttu-id="2cc99-114">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2cc99-114">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
