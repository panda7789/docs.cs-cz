---
title: "ICorDebugVariableHome::GetCode – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6fccbd05ac03aca640e3f847abaa68ca84949110
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablehomegetcode-method"></a><span data-ttu-id="c4f04-102">ICorDebugVariableHome::GetCode – metoda</span><span class="sxs-lookup"><span data-stu-id="c4f04-102">ICorDebugVariableHome::GetCode Method</span></span>
<span data-ttu-id="c4f04-103">Získá instanci "ICorDebugCode", která obsahuje toto [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="c4f04-103">Gets the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4f04-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4f04-104">Syntax</span></span>  
  
```  
HRESULT GetCode(  
    [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c4f04-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c4f04-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="c4f04-106">[out] Ukazatel na adresu "ICorDebugCode" instanci, která obsahuje toto [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="c4f04-106">[out] A pointer to the address of the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4f04-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c4f04-107">Requirements</span></span>  
 <span data-ttu-id="c4f04-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4f04-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4f04-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4f04-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4f04-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4f04-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4f04-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4f04-111">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4f04-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="c4f04-112">See Also</span></span>  
 [<span data-ttu-id="c4f04-113">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c4f04-113">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 
