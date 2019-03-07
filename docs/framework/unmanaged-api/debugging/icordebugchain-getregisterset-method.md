---
title: ICorDebugChain::GetRegisterSet – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetRegisterSet
helpviewer_keywords:
- ICorDebugChain::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: bc4288b6-3331-4ae3-990d-e1d6e62ecb67
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f366a40e1e3cd196f480c5849c49419c7daeea9e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480985"
---
# <a name="icordebugchaingetregisterset-method"></a><span data-ttu-id="1fd43-102">ICorDebugChain::GetRegisterSet – metoda</span><span class="sxs-lookup"><span data-stu-id="1fd43-102">ICorDebugChain::GetRegisterSet Method</span></span>
<span data-ttu-id="1fd43-103">Získá do registru pro aktivní součástí tohoto řetězce.</span><span class="sxs-lookup"><span data-stu-id="1fd43-103">Gets the register set for the active part of this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fd43-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1fd43-104">Syntax</span></span>  
  
```  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1fd43-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1fd43-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="1fd43-106">[out] Ukazatel na adresu [icordebugregisterset –](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) nastavit objekt, který reprezentuje do registru pro aktivní součástí tohoto řetězce.</span><span class="sxs-lookup"><span data-stu-id="1fd43-106">[out] A pointer to the address of an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) object that represents the register set for the active part of this chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fd43-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1fd43-107">Requirements</span></span>  
 <span data-ttu-id="1fd43-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1fd43-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fd43-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1fd43-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1fd43-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1fd43-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1fd43-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fd43-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
