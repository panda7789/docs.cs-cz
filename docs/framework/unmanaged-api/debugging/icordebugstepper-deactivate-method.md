---
title: ICorDebugStepper::Deactivate – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.Deactivate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Deactivate
helpviewer_keywords:
- Deactivate method [.NET Framework debugging]
- ICorDebugStepper::Deactivate method [.NET Framework debugging]
ms.assetid: 855f4199-b62d-40ce-998e-1eb4a1772142
topic_type:
- apiref
ms.openlocfilehash: 760f69baf311cf320e9c358ba1c45c942934f1a5
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379399"
---
# <a name="icordebugstepperdeactivate-method"></a><span data-ttu-id="7e7e3-102">ICorDebugStepper::Deactivate – metoda</span><span class="sxs-lookup"><span data-stu-id="7e7e3-102">ICorDebugStepper::Deactivate Method</span></span>
<span data-ttu-id="7e7e3-103">Způsobí, že tato ICorDebugStepper zruší příkaz posledního kroku, který přijal.</span><span class="sxs-lookup"><span data-stu-id="7e7e3-103">Causes this ICorDebugStepper to cancel the last step command that it received.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e7e3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e7e3-104">Syntax</span></span>  
  
```cpp  
HRESULT Deactivate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="7e7e3-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7e7e3-105">Remarks</span></span>  
 <span data-ttu-id="7e7e3-106">Nový příkaz pro krokování může být vydán po zrušení příkazu poslední přijatý krok.</span><span class="sxs-lookup"><span data-stu-id="7e7e3-106">A new stepping command may be issued after the most recently received step command has been canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e7e3-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7e7e3-107">Requirements</span></span>  
 <span data-ttu-id="7e7e3-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e7e3-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e7e3-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7e7e3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e7e3-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7e7e3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e7e3-111">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e7e3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
