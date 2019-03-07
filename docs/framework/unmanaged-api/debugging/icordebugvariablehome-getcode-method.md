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
ms.openlocfilehash: 6c9b334535f8f6652f30a4b5c9de64bde435c3bd
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496219"
---
# <a name="icordebugvariablehomegetcode-method"></a><span data-ttu-id="aea86-102">ICorDebugVariableHome::GetCode – metoda</span><span class="sxs-lookup"><span data-stu-id="aea86-102">ICorDebugVariableHome::GetCode Method</span></span>
<span data-ttu-id="aea86-103">Získá instanci "ICorDebugCode", která obsahuje tato [icordebugvariablehome –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="aea86-103">Gets the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aea86-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aea86-104">Syntax</span></span>  
  
```  
HRESULT GetCode(  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aea86-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aea86-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="aea86-106">[out] Ukazatel na adresu "ICorDebugCode" instanci, která obsahuje tato [icordebugvariablehome –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="aea86-106">[out] A pointer to the address of the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aea86-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aea86-107">Requirements</span></span>  
 <span data-ttu-id="aea86-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aea86-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aea86-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aea86-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aea86-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aea86-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aea86-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aea86-111">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aea86-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aea86-112">See also</span></span>
- [<span data-ttu-id="aea86-113">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aea86-113">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)

