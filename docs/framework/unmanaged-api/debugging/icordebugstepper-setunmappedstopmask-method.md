---
title: ICorDebugStepper::SetUnmappedStopMask – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetUnmappedStopMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetUnmappedStopMask
helpviewer_keywords:
- ICorDebugStepper::SetUnmappedStopMask method [.NET Framework debugging]
- SetUnmappedStopMask method [.NET Framework debugging]
ms.assetid: b1211981-e90c-4e05-8def-fa18d85ad9ab
topic_type:
- apiref
ms.openlocfilehash: ff393b119c349e34898b781c3185cc82f2dba11f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137556"
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a><span data-ttu-id="07baa-102">ICorDebugStepper::SetUnmappedStopMask – metoda</span><span class="sxs-lookup"><span data-stu-id="07baa-102">ICorDebugStepper::SetUnmappedStopMask Method</span></span>
<span data-ttu-id="07baa-103">Nastaví hodnotu, která určuje typ nemapovaného kódu, ve kterém se spuštění zastaví.</span><span class="sxs-lookup"><span data-stu-id="07baa-103">Sets a value that specifies the type of unmapped code in which execution will halt.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07baa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07baa-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07baa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="07baa-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="07baa-106">pro Hodnota výčtu CorDebugUnmappedStop –, která určuje typ nemapovaného kódu, ve kterém ladicí program zastaví provádění.</span><span class="sxs-lookup"><span data-stu-id="07baa-106">[in] A value of the CorDebugUnmappedStop enumeration that specifies the type of unmapped code in which the debugger will halt execution.</span></span>  
  
 <span data-ttu-id="07baa-107">Výchozí hodnota je STOP_OTHER_UNMAPPED.</span><span class="sxs-lookup"><span data-stu-id="07baa-107">The default value is STOP_OTHER_UNMAPPED.</span></span> <span data-ttu-id="07baa-108">Hodnota STOP_UNMANAGED je platná pouze s laděním spolupráce.</span><span class="sxs-lookup"><span data-stu-id="07baa-108">The value STOP_UNMANAGED is only valid with interop debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07baa-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="07baa-109">Remarks</span></span>  
 <span data-ttu-id="07baa-110">Když ladicí program najde kompilaci za běhu (JIT), která nemá žádné odpovídající mapování na jazyk MSIL (Microsoft Intermediate Language), zastaví provádění, pokud byl nastaven příznak určující tento typ nemapovaného kódu; v opačném případě pokračuje krokování transparentně.</span><span class="sxs-lookup"><span data-stu-id="07baa-110">When the debugger finds a just-in-time (JIT) compilation that has no corresponding mapping to Microsoft intermediate language (MSIL), it halts execution if the flag specifying that type of unmapped code has been set; otherwise, stepping transparently continues.</span></span>  
  
 <span data-ttu-id="07baa-111">Pokud ladicí program nepoužívá stepper k zadání metody, pak nebude nutně Krokovat s nemapovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="07baa-111">If the debugger doesn't use a stepper to enter a method, then it won't necessarily step over unmapped code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07baa-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="07baa-112">Requirements</span></span>  
 <span data-ttu-id="07baa-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07baa-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07baa-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="07baa-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="07baa-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="07baa-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07baa-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07baa-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
