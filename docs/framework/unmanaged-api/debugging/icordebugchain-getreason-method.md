---
title: ICorDebugChain::GetReason – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- GetReason
helpviewer_keywords:
- GetReason method [.NET Framework debugging]
- ICorDebugChain::GetReason method [.NET Framework debugging]
ms.assetid: 9f9f62b9-113a-4a98-8f9b-b593cef27b03
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e5120b5fddf621d6f4c684c4c432fda4f5c0117
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745253"
---
# <a name="icordebugchaingetreason-method"></a><span data-ttu-id="e2f84-102">ICorDebugChain::GetReason – metoda</span><span class="sxs-lookup"><span data-stu-id="e2f84-102">ICorDebugChain::GetReason Method</span></span>
<span data-ttu-id="e2f84-103">Získá důvod genesis tento řetěz volání.</span><span class="sxs-lookup"><span data-stu-id="e2f84-103">Gets the reason for the genesis of this calling chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2f84-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2f84-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReason (  
    [out] CorDebugChainReason *pReason  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2f84-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e2f84-105">Parameters</span></span>  
 `pReason`  
 <span data-ttu-id="e2f84-106">[out] Ukazatel na hodnotu (bitová kombinace) cordebugchainreason – výčet, který označuje důvod genesis tento řetěz volání.</span><span class="sxs-lookup"><span data-stu-id="e2f84-106">[out] A pointer to a value (a bitwise combination) of the CorDebugChainReason enumeration that indicates the reason for the genesis of this calling chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2f84-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e2f84-107">Requirements</span></span>  
 <span data-ttu-id="e2f84-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2f84-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2f84-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e2f84-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e2f84-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2f84-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2f84-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2f84-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
