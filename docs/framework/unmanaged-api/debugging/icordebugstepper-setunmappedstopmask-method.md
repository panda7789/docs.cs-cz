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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0a273c54559e8e297e09740ba9c770ce12d72d1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760580"
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a><span data-ttu-id="14874-102">ICorDebugStepper::SetUnmappedStopMask – metoda</span><span class="sxs-lookup"><span data-stu-id="14874-102">ICorDebugStepper::SetUnmappedStopMask Method</span></span>
<span data-ttu-id="14874-103">Nastaví hodnotu, která určuje typ nenamapované kódu, ve kterém se zastaví provádění.</span><span class="sxs-lookup"><span data-stu-id="14874-103">Sets a value that specifies the type of unmapped code in which execution will halt.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14874-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14874-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14874-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="14874-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="14874-106">[in] Hodnota cordebugunmappedstop – výčet, který určuje typ nenamapované kódu, ve kterém se ladicí program zastaví provádění.</span><span class="sxs-lookup"><span data-stu-id="14874-106">[in] A value of the CorDebugUnmappedStop enumeration that specifies the type of unmapped code in which the debugger will halt execution.</span></span>  
  
 <span data-ttu-id="14874-107">Výchozí hodnota je STOP_OTHER_UNMAPPED.</span><span class="sxs-lookup"><span data-stu-id="14874-107">The default value is STOP_OTHER_UNMAPPED.</span></span> <span data-ttu-id="14874-108">Hodnota STOP_UNMANAGED je platný pouze s definiční ladění.</span><span class="sxs-lookup"><span data-stu-id="14874-108">The value STOP_UNMANAGED is only valid with interop debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14874-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="14874-109">Remarks</span></span>  
 <span data-ttu-id="14874-110">Pokud ladicí program nalezne kompilace just-in-time (JIT), který nemá žádné odpovídající mapování pro jazyk Microsoft intermediate language (MSIL), se zastaví spuštění, pokud byl nastaven příznak určení typu nenamapované kódu; v opačném případě krokování transparentně bude pokračovat.</span><span class="sxs-lookup"><span data-stu-id="14874-110">When the debugger finds a just-in-time (JIT) compilation that has no corresponding mapping to Microsoft intermediate language (MSIL), it halts execution if the flag specifying that type of unmapped code has been set; otherwise, stepping transparently continues.</span></span>  
  
 <span data-ttu-id="14874-111">Pokud ladicí program nepoužívá krokovač zadejte metodu, pak jej nebude krok nutně přes nenamapované kódu.</span><span class="sxs-lookup"><span data-stu-id="14874-111">If the debugger doesn't use a stepper to enter a method, then it won't necessarily step over unmapped code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14874-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="14874-112">Requirements</span></span>  
 <span data-ttu-id="14874-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14874-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14874-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="14874-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14874-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14874-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14874-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14874-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
