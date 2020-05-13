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
ms.openlocfilehash: 843c6df1ef41fdd3227b92275182432ad4cc43b1
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379730"
---
# <a name="icordebugthreadgetactiveframe-method"></a><span data-ttu-id="ed87a-102">ICorDebugThread::GetActiveFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="ed87a-102">ICorDebugThread::GetActiveFrame Method</span></span>
<span data-ttu-id="ed87a-103">Získá ukazatel rozhraní na aktivní (poslední) rámec na tomto objektu ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="ed87a-103">Gets an interface pointer to the active (most recent) frame on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed87a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed87a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed87a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ed87a-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="ed87a-106">mimo Ukazatel na adresu objektu rozhraní ICorDebugFrame, který představuje rámec.</span><span class="sxs-lookup"><span data-stu-id="ed87a-106">[out] A pointer to the address of an ICorDebugFrame interface object that represents a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed87a-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ed87a-107">Remarks</span></span>  
 <span data-ttu-id="ed87a-108">`ppFrame`Pokud není žádný rámec aktuálně aktivní, parametr má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="ed87a-108">The `ppFrame` parameter is null if no frame is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed87a-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ed87a-109">Requirements</span></span>  
 <span data-ttu-id="ed87a-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed87a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed87a-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ed87a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ed87a-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ed87a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed87a-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed87a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
