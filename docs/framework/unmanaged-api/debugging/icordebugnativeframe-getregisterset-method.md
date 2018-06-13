---
title: ICorDebugNativeFrame::GetRegisterSet – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetRegisterSet
helpviewer_keywords:
- ICorDebugNativeFrame::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 6f309b5f-5556-4f1e-b1dd-4fe97fc81d01
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6880ed3a2519ad7d4a415e4fcc4510668a0852f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416703"
---
# <a name="icordebugnativeframegetregisterset-method"></a><span data-ttu-id="cbb2a-102">ICorDebugNativeFrame::GetRegisterSet – metoda</span><span class="sxs-lookup"><span data-stu-id="cbb2a-102">ICorDebugNativeFrame::GetRegisterSet Method</span></span>
<span data-ttu-id="cbb2a-103">Získá zaregistrovat, nastavte pro tento rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="cbb2a-103">Gets the register set for this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbb2a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cbb2a-104">Syntax</span></span>  
  
```  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cbb2a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cbb2a-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="cbb2a-106">[out] Ukazatel na adresu [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) objekt, který reprezentuje rejstříku nastavte pro tento rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="cbb2a-106">[out] A pointer to the address of an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) object that represents the register set for this stack frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbb2a-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cbb2a-107">Requirements</span></span>  
 <span data-ttu-id="cbb2a-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbb2a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbb2a-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cbb2a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cbb2a-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cbb2a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cbb2a-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbb2a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbb2a-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="cbb2a-112">See Also</span></span>  
 
