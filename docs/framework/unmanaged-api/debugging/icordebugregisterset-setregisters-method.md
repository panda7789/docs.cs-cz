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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d17c353d8e2358a1651ba3fbbb1dd718cc681f7b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59123790"
---
# <a name="icordebugregistersetsetregisters-method"></a><span data-ttu-id="9b025-102">ICorDebugRegisterSet::SetRegisters – metoda</span><span class="sxs-lookup"><span data-stu-id="9b025-102">ICorDebugRegisterSet::SetRegisters Method</span></span>
`SetRegisters` <span data-ttu-id="9b025-103">není implementováno v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="9b025-103">is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="9b025-104">Nevolejte tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="9b025-104">Do not call this method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b025-105">Pomocí operace vyšší úrovně, jako [icordebugilframe::setip –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) nebo [icordebugnativeframe::setip –](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md).</span><span class="sxs-lookup"><span data-stu-id="9b025-105">Use the higher-level operations such as [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) or [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b025-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b025-106">Syntax</span></span>  
  
```  
HRESULT SetRegisters (  
    [in] ULONG64   mask,  
    [in] ULONG32   regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="9b025-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9b025-107">Requirements</span></span>  
 <span data-ttu-id="9b025-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b025-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b025-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b025-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b025-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b025-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b025-111">**Verze rozhraní .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="9b025-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b025-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9b025-112">See also</span></span>

- [<span data-ttu-id="9b025-113">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9b025-113">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="9b025-114">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9b025-114">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
