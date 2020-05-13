---
title: ICorDebugThread::GetActiveChain – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetActiveChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetActiveChain
helpviewer_keywords:
- ICorDebugThread::GetActiveChain method [.NET Framework debugging]
- GetActiveChain method [.NET Framework debugging]
ms.assetid: f50de1f7-40ef-4949-b542-1d9a61f7bfef
topic_type:
- apiref
ms.openlocfilehash: 70e79378ad8eb2599199a1f7bc57cf530c9b4dd3
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379684"
---
# <a name="icordebugthreadgetactivechain-method"></a><span data-ttu-id="c802f-102">ICorDebugThread::GetActiveChain – metoda</span><span class="sxs-lookup"><span data-stu-id="c802f-102">ICorDebugThread::GetActiveChain Method</span></span>
<span data-ttu-id="c802f-103">Získá ukazatel rozhraní na aktivní (nejnovější) řetěz zásobníku na tomto objektu ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="c802f-103">Gets an interface pointer to the active (most recent) stack chain on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c802f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c802f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveChain (  
    [out] ICorDebugChain **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c802f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c802f-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="c802f-106">mimo Ukazatel na adresu objektu ICorDebugChain, který představuje řetěz zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c802f-106">[out] A pointer to the address of an ICorDebugChain object that represents the stack chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c802f-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c802f-107">Remarks</span></span>  
 <span data-ttu-id="c802f-108">`ppChain`Parametr má hodnotu null, pokud není aktuálně aktivní žádný řetěz zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c802f-108">The `ppChain` parameter is null if no stack chain is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c802f-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c802f-109">Requirements</span></span>  
 <span data-ttu-id="c802f-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c802f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c802f-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c802f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c802f-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c802f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c802f-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c802f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
