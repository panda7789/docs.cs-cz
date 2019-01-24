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
ms.openlocfilehash: 216779ab03b426ceb8003accfbdd182f583b77cc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557341"
---
# <a name="icordebugvariablehomegetcode-method"></a><span data-ttu-id="f8c60-102">ICorDebugVariableHome::GetCode – metoda</span><span class="sxs-lookup"><span data-stu-id="f8c60-102">ICorDebugVariableHome::GetCode Method</span></span>
<span data-ttu-id="f8c60-103">Získá instanci "ICorDebugCode", která obsahuje tato [icordebugvariablehome –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="f8c60-103">Gets the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8c60-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8c60-104">Syntax</span></span>  
  
```  
HRESULT GetCode(  
    [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f8c60-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8c60-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="f8c60-106">[out] Ukazatel na adresu "ICorDebugCode" instanci, která obsahuje tato [icordebugvariablehome –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="f8c60-106">[out] A pointer to the address of the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8c60-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f8c60-107">Requirements</span></span>  
 <span data-ttu-id="f8c60-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8c60-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8c60-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f8c60-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8c60-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8c60-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8c60-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8c60-111">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8c60-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8c60-112">See also</span></span>
- [<span data-ttu-id="f8c60-113">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f8c60-113">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)

