---
title: ICorDebugChain::GetPrevious – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetPrevious
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetPrevious
helpviewer_keywords:
- ICorDebugChain::GetPrevious method [.NET Framework debugging]
- GetPrevious method [.NET Framework debugging]
ms.assetid: 58eed4c8-d80c-4c6a-a875-967a90dd926c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31c795c2fbbfdc45b6e1aac6684f730f55fc106a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746415"
---
# <a name="icordebugchaingetprevious-method"></a><span data-ttu-id="cce04-102">ICorDebugChain::GetPrevious – metoda</span><span class="sxs-lookup"><span data-stu-id="cce04-102">ICorDebugChain::GetPrevious Method</span></span>
<span data-ttu-id="cce04-103">Získá předchozí řetězu rámce pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="cce04-103">Gets the previous chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cce04-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cce04-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPrevious (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cce04-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cce04-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="cce04-106">[out] Ukazatel na adresa icordebugchain – objekt, který představuje předchozí řetězu snímků pro toto vlákno.</span><span class="sxs-lookup"><span data-stu-id="cce04-106">[out] A pointer to the address of an ICorDebugChain object that represents the previous chain of frames for this thread.</span></span> <span data-ttu-id="cce04-107">Pokud se tento řetězec je první řetězec `ppChain` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="cce04-107">If this chain is the first chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cce04-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cce04-108">Requirements</span></span>  
 <span data-ttu-id="cce04-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cce04-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cce04-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cce04-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cce04-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cce04-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cce04-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cce04-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
