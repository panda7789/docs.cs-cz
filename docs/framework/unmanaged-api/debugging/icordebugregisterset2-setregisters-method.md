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
ms.openlocfilehash: 4f7ba8228ae47508e3aa3ac79cf635fcf4eba329
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604428"
---
# <a name="icordebugregisterset2setregisters-method"></a><span data-ttu-id="66416-102">ICorDebugRegisterSet2::SetRegisters – metoda</span><span class="sxs-lookup"><span data-stu-id="66416-102">ICorDebugRegisterSet2::SetRegisters Method</span></span>
<span data-ttu-id="66416-103">`SetRegisters` není implementováno v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="66416-103">`SetRegisters` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="66416-104">Nevolejte tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="66416-104">Do not call this method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="66416-105">Pomocí operace vyšší úrovně, jako [icordebugilframe::setip –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) nebo [icordebugnativeframe::setip –](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md).</span><span class="sxs-lookup"><span data-stu-id="66416-105">Use the higher-level operations such as [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) or [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66416-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66416-106">Syntax</span></span>  
  
```  
HRESULT SetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="66416-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66416-107">Requirements</span></span>  
 <span data-ttu-id="66416-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66416-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66416-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="66416-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66416-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66416-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66416-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66416-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66416-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66416-112">See also</span></span>
- [<span data-ttu-id="66416-113">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66416-113">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [<span data-ttu-id="66416-114">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66416-114">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
