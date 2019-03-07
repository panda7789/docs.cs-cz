---
title: ICorDebugChain::EnumerateFrames – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.EnumerateFrames
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::EnumerateFrames method
helpviewer_keywords:
- EnumerateFrames method [.NET Framework debugging]
- ICorDebugChain::EnumerateFrames method [.NET Framework debugging]
ms.assetid: 9fcefa98-750d-4168-8915-8173a43accf2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7568f8ca3b92ef465ab595348f68895f389d61e4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489706"
---
# <a name="icordebugchainenumerateframes-method"></a><span data-ttu-id="9d449-102">ICorDebugChain::EnumerateFrames – metoda</span><span class="sxs-lookup"><span data-stu-id="9d449-102">ICorDebugChain::EnumerateFrames Method</span></span>
<span data-ttu-id="9d449-103">Získá enumerátor, který obsahuje všechny rámce zásobníku spravovaného v řetězci, od posledního rámce.</span><span class="sxs-lookup"><span data-stu-id="9d449-103">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d449-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d449-104">Syntax</span></span>  
  
```  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d449-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d449-105">Parameters</span></span>  
 `ppFrames`  
 <span data-ttu-id="9d449-106">[out] Ukazatel na adresu icordebugframeenum – objekt, který je čítač pro rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="9d449-106">[out] A pointer to the address of an ICorDebugFrameEnum object that is the enumerator for the stack frames.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d449-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9d449-107">Remarks</span></span>  
 <span data-ttu-id="9d449-108">Řetězec představuje fyzické volání zásobníku pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="9d449-108">The chain represents the physical call stack for the thread.</span></span>  
  
 <span data-ttu-id="9d449-109">`EnumerateFrames` Metodu lze volat pouze pro spravované řetězce.</span><span class="sxs-lookup"><span data-stu-id="9d449-109">The `EnumerateFrames` method should be called only for managed chains.</span></span> <span data-ttu-id="9d449-110">Rozhraní API pro ladění neposkytuje metody pro získání snímky obsažené v nespravované řetězců.</span><span class="sxs-lookup"><span data-stu-id="9d449-110">The debugging API does not provide methods for obtaining frames contained in unmanaged chains.</span></span> <span data-ttu-id="9d449-111">Ladicí program musí používat další prostředky pro získání těchto informací.</span><span class="sxs-lookup"><span data-stu-id="9d449-111">The debugger must use other means to obtain this information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d449-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9d449-112">Requirements</span></span>  
 <span data-ttu-id="9d449-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d449-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d449-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9d449-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d449-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d449-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d449-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d449-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
