---
title: ICorDebugThread::GetActiveFrame – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetActiveFrame
helpviewer_keywords:
- ICorDebugThread::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 8d6d3a1a-fef6-4f2f-a22c-3bdd30d70e07
topic_type:
- apiref
ms.openlocfilehash: d623893bd77e46832b0bd823ed60c23e4eee29ba
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133543"
---
# <a name="icordebugthreadgetactiveframe-method"></a><span data-ttu-id="b7a91-102">ICorDebugThread::GetActiveFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="b7a91-102">ICorDebugThread::GetActiveFrame Method</span></span>
<span data-ttu-id="b7a91-103">Získá ukazatel rozhraní na aktivní (poslední) rámec na tomto objektu ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="b7a91-103">Gets an interface pointer to the active (most recent) frame on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7a91-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7a91-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7a91-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b7a91-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="b7a91-106">mimo Ukazatel na adresu objektu rozhraní ICorDebugFrame, který představuje rámec.</span><span class="sxs-lookup"><span data-stu-id="b7a91-106">[out] A pointer to the address of an ICorDebugFrame interface object that represents a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7a91-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b7a91-107">Remarks</span></span>  
 <span data-ttu-id="b7a91-108">Parametr `ppFrame` má hodnotu null, pokud není aktuálně aktivní žádný rámec.</span><span class="sxs-lookup"><span data-stu-id="b7a91-108">The `ppFrame` parameter is null if no frame is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7a91-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b7a91-109">Requirements</span></span>  
 <span data-ttu-id="b7a91-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7a91-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7a91-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b7a91-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7a91-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b7a91-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7a91-113">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7a91-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
