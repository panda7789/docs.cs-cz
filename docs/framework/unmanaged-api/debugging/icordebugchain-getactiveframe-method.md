---
title: "ICorDebugChain::GetActiveFrame – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.GetActiveFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::GetActiveFrame
helpviewer_keywords:
- ICorDebugChain::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 36887017-670b-4f21-b406-8fab956f84a3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b5de327c1579d05f6ae4a440fc76a3fb9ee99b13
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugchaingetactiveframe-method"></a><span data-ttu-id="578b4-102">ICorDebugChain::GetActiveFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="578b4-102">ICorDebugChain::GetActiveFrame Method</span></span>
<span data-ttu-id="578b4-103">Získá aktivní (tedy poslední) rámce v řetězu.</span><span class="sxs-lookup"><span data-stu-id="578b4-103">Gets the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="578b4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="578b4-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="578b4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="578b4-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="578b4-106">[out] Ukazatel na adresu ICorDebugFrame objekt, který představuje aktivní (tedy poslední) rámce v řetězu.</span><span class="sxs-lookup"><span data-stu-id="578b4-106">[out] A pointer to the address of an ICorDebugFrame object that represents the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="578b4-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="578b4-107">Remarks</span></span>  
 <span data-ttu-id="578b4-108">Pokud je k dispozici, žádné spravované zásobníku `ppFrame` je nastaven na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="578b4-108">If no managed stack frame is available, `ppFrame` is set to null.</span></span>  
  
 <span data-ttu-id="578b4-109">Pokud aktivní rámečku není k dispozici, volání bude úspěšné a `ppFrame` bude mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="578b4-109">If the active frame is not available, the call will succeed and `ppFrame` will be null.</span></span> <span data-ttu-id="578b4-110">Aktivní rámce nebudete mít k dispozici pro řetězy inicializovat z důvodu CHAIN_ENTER_UNMANAGED a některé řetězy inicializovat z důvodu CHAIN_CLASS_INIT.</span><span class="sxs-lookup"><span data-stu-id="578b4-110">Active frames will not be available for chains initiated due to CHAIN_ENTER_UNMANAGED, and for some chains initiated due to CHAIN_CLASS_INIT.</span></span> <span data-ttu-id="578b4-111">V tématu CorDebugChainReason – výčet.</span><span class="sxs-lookup"><span data-stu-id="578b4-111">See the CorDebugChainReason enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="578b4-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="578b4-112">Requirements</span></span>  
 <span data-ttu-id="578b4-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="578b4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="578b4-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="578b4-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="578b4-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="578b4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="578b4-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="578b4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
