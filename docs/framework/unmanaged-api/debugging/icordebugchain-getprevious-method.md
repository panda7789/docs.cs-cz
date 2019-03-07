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
ms.openlocfilehash: 7fdcdf23dfee01e8bad1c95adb4de66f270d5e00
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474966"
---
# <a name="icordebugchaingetprevious-method"></a><span data-ttu-id="51b80-102">ICorDebugChain::GetPrevious – metoda</span><span class="sxs-lookup"><span data-stu-id="51b80-102">ICorDebugChain::GetPrevious Method</span></span>
<span data-ttu-id="51b80-103">Získá předchozí řetězu rámce pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="51b80-103">Gets the previous chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51b80-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51b80-104">Syntax</span></span>  
  
```  
HRESULT GetPrevious (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51b80-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="51b80-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="51b80-106">[out] Ukazatel na adresa icordebugchain – objekt, který představuje předchozí řetězu snímků pro toto vlákno.</span><span class="sxs-lookup"><span data-stu-id="51b80-106">[out] A pointer to the address of an ICorDebugChain object that represents the previous chain of frames for this thread.</span></span> <span data-ttu-id="51b80-107">Pokud se tento řetězec je první řetězec `ppChain` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="51b80-107">If this chain is the first chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51b80-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="51b80-108">Requirements</span></span>  
 <span data-ttu-id="51b80-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51b80-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51b80-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="51b80-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51b80-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51b80-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51b80-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51b80-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
