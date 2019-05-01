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
ms.openlocfilehash: 48650a370f7d15724e20850e9d3b47dc8215f960
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989492"
---
# <a name="icordebugchaingetreason-method"></a><span data-ttu-id="3fd68-102">ICorDebugChain::GetReason – metoda</span><span class="sxs-lookup"><span data-stu-id="3fd68-102">ICorDebugChain::GetReason Method</span></span>
<span data-ttu-id="3fd68-103">Získá důvod genesis tento řetěz volání.</span><span class="sxs-lookup"><span data-stu-id="3fd68-103">Gets the reason for the genesis of this calling chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fd68-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3fd68-104">Syntax</span></span>  
  
```  
HRESULT GetReason (  
    [out] CorDebugChainReason *pReason  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fd68-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3fd68-105">Parameters</span></span>  
 `pReason`  
 <span data-ttu-id="3fd68-106">[out] Ukazatel na hodnotu (bitová kombinace) cordebugchainreason – výčet, který označuje důvod genesis tento řetěz volání.</span><span class="sxs-lookup"><span data-stu-id="3fd68-106">[out] A pointer to a value (a bitwise combination) of the CorDebugChainReason enumeration that indicates the reason for the genesis of this calling chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fd68-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3fd68-107">Requirements</span></span>  
 <span data-ttu-id="3fd68-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fd68-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fd68-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3fd68-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3fd68-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3fd68-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3fd68-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fd68-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
