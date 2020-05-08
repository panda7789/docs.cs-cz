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
ms.openlocfilehash: c8a62d8b4a4db0f36d991c32dbfc5bad68780f1b
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894698"
---
# <a name="icordebugchainenumerateframes-method"></a><span data-ttu-id="0bd1f-102">ICorDebugChain::EnumerateFrames – metoda</span><span class="sxs-lookup"><span data-stu-id="0bd1f-102">ICorDebugChain::EnumerateFrames Method</span></span>
<span data-ttu-id="0bd1f-103">Získá enumerátor, který obsahuje všechny spravované rámce zásobníku v řetězci počínaje posledním rámcem.</span><span class="sxs-lookup"><span data-stu-id="0bd1f-103">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bd1f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0bd1f-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0bd1f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0bd1f-105">Parameters</span></span>  
 `ppFrames`  
 <span data-ttu-id="0bd1f-106">mimo Ukazatel na adresu objektu ICorDebugFrameEnum, který je enumerátorem pro rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="0bd1f-106">[out] A pointer to the address of an ICorDebugFrameEnum object that is the enumerator for the stack frames.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0bd1f-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0bd1f-107">Remarks</span></span>  
 <span data-ttu-id="0bd1f-108">Řetěz představuje fyzický zásobník volání pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="0bd1f-108">The chain represents the physical call stack for the thread.</span></span>  
  
 <span data-ttu-id="0bd1f-109">`EnumerateFrames` Metoda by měla být volána pouze pro spravované řetězy.</span><span class="sxs-lookup"><span data-stu-id="0bd1f-109">The `EnumerateFrames` method should be called only for managed chains.</span></span> <span data-ttu-id="0bd1f-110">Rozhraní API pro ladění neposkytuje metody pro získání rámců obsažených v nespravovaných řetězcích.</span><span class="sxs-lookup"><span data-stu-id="0bd1f-110">The debugging API does not provide methods for obtaining frames contained in unmanaged chains.</span></span> <span data-ttu-id="0bd1f-111">K získání těchto informací musí ladicí program použít jiný způsob.</span><span class="sxs-lookup"><span data-stu-id="0bd1f-111">The debugger must use other means to obtain this information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bd1f-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0bd1f-112">Requirements</span></span>  
 <span data-ttu-id="0bd1f-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0bd1f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bd1f-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0bd1f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0bd1f-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0bd1f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0bd1f-116">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bd1f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
