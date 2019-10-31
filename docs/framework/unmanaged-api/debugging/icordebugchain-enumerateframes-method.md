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
ms.openlocfilehash: 0b024d3396dfe1796fcb18afa122d4aee39c4ccc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132726"
---
# <a name="icordebugchainenumerateframes-method"></a><span data-ttu-id="7d492-102">ICorDebugChain::EnumerateFrames – metoda</span><span class="sxs-lookup"><span data-stu-id="7d492-102">ICorDebugChain::EnumerateFrames Method</span></span>
<span data-ttu-id="7d492-103">Získá enumerátor, který obsahuje všechny spravované rámce zásobníku v řetězci počínaje posledním rámcem.</span><span class="sxs-lookup"><span data-stu-id="7d492-103">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d492-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d492-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d492-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d492-105">Parameters</span></span>  
 `ppFrames`  
 <span data-ttu-id="7d492-106">mimo Ukazatel na adresu objektu ICorDebugFrameEnum, který je enumerátorem pro rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="7d492-106">[out] A pointer to the address of an ICorDebugFrameEnum object that is the enumerator for the stack frames.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d492-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d492-107">Remarks</span></span>  
 <span data-ttu-id="7d492-108">Řetěz představuje fyzický zásobník volání pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="7d492-108">The chain represents the physical call stack for the thread.</span></span>  
  
 <span data-ttu-id="7d492-109">Metoda `EnumerateFrames` by měla být volána pouze pro spravované řetězy.</span><span class="sxs-lookup"><span data-stu-id="7d492-109">The `EnumerateFrames` method should be called only for managed chains.</span></span> <span data-ttu-id="7d492-110">Rozhraní API pro ladění neposkytuje metody pro získání rámců obsažených v nespravovaných řetězcích.</span><span class="sxs-lookup"><span data-stu-id="7d492-110">The debugging API does not provide methods for obtaining frames contained in unmanaged chains.</span></span> <span data-ttu-id="7d492-111">K získání těchto informací musí ladicí program použít jiný způsob.</span><span class="sxs-lookup"><span data-stu-id="7d492-111">The debugger must use other means to obtain this information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d492-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d492-112">Requirements</span></span>  
 <span data-ttu-id="7d492-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d492-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d492-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7d492-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d492-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7d492-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d492-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d492-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
