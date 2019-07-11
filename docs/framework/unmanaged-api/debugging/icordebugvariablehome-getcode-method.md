---
title: ICorDebugVariableHome::GetCode – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetCode
helpviewer_keywords:
- ICorDebugVariableHome::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: ef002890-4a7b-4a5d-abbf-16c60083f794
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c0cae29cceb3f23c7d09cf096937c99641d5a87
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773600"
---
# <a name="icordebugvariablehomegetcode-method"></a><span data-ttu-id="33d0e-102">ICorDebugVariableHome::GetCode – metoda</span><span class="sxs-lookup"><span data-stu-id="33d0e-102">ICorDebugVariableHome::GetCode Method</span></span>
<span data-ttu-id="33d0e-103">Získá instanci "ICorDebugCode", která obsahuje tato [icordebugvariablehome –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="33d0e-103">Gets the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33d0e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33d0e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33d0e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="33d0e-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="33d0e-106">[out] Ukazatel na adresu "ICorDebugCode" instanci, která obsahuje tato [icordebugvariablehome –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="33d0e-106">[out] A pointer to the address of the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33d0e-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="33d0e-107">Requirements</span></span>  
 <span data-ttu-id="33d0e-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33d0e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33d0e-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="33d0e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33d0e-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33d0e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33d0e-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33d0e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33d0e-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="33d0e-112">See also</span></span>

- [<span data-ttu-id="33d0e-113">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="33d0e-113">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
