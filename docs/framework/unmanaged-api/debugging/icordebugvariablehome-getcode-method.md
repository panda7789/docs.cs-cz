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
ms.openlocfilehash: ee8fa8feebba7258fc84ee7ba00ce2ab1977faa4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420401"
---
# <a name="icordebugvariablehomegetcode-method"></a><span data-ttu-id="1d7ce-102">ICorDebugVariableHome::GetCode – metoda</span><span class="sxs-lookup"><span data-stu-id="1d7ce-102">ICorDebugVariableHome::GetCode Method</span></span>
<span data-ttu-id="1d7ce-103">Získá instanci "ICorDebugCode", která obsahuje toto [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="1d7ce-103">Gets the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d7ce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d7ce-104">Syntax</span></span>  
  
```  
HRESULT GetCode(  
    [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1d7ce-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1d7ce-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="1d7ce-106">[out] Ukazatel na adresu "ICorDebugCode" instanci, která obsahuje toto [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="1d7ce-106">[out] A pointer to the address of the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d7ce-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1d7ce-107">Requirements</span></span>  
 <span data-ttu-id="1d7ce-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d7ce-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d7ce-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1d7ce-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d7ce-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d7ce-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d7ce-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d7ce-111">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d7ce-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="1d7ce-112">See Also</span></span>  
 [<span data-ttu-id="1d7ce-113">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1d7ce-113">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 
