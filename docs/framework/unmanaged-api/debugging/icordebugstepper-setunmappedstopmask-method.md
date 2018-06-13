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
ms.openlocfilehash: dc4e51ec60c7526f36bbe4909bec91a527e0862c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419907"
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a><span data-ttu-id="3c2cb-102">ICorDebugStepper::SetUnmappedStopMask – metoda</span><span class="sxs-lookup"><span data-stu-id="3c2cb-102">ICorDebugStepper::SetUnmappedStopMask Method</span></span>
<span data-ttu-id="3c2cb-103">Nastaví hodnotu, která určuje typ nenamapovaný kódu, ve kterém se zastaví provádění.</span><span class="sxs-lookup"><span data-stu-id="3c2cb-103">Sets a value that specifies the type of unmapped code in which execution will halt.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c2cb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c2cb-104">Syntax</span></span>  
  
```  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3c2cb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3c2cb-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="3c2cb-106">[v] Hodnota CorDebugUnmappedStop – výčet, který určuje typ nenamapovaný kódu, ve kterém bude zastavení ladicího programu provádění.</span><span class="sxs-lookup"><span data-stu-id="3c2cb-106">[in] A value of the CorDebugUnmappedStop enumeration that specifies the type of unmapped code in which the debugger will halt execution.</span></span>  
  
 <span data-ttu-id="3c2cb-107">Výchozí hodnota je STOP_OTHER_UNMAPPED.</span><span class="sxs-lookup"><span data-stu-id="3c2cb-107">The default value is STOP_OTHER_UNMAPPED.</span></span> <span data-ttu-id="3c2cb-108">Hodnota STOP_UNMANAGED je platný pouze s spolupráce ladění.</span><span class="sxs-lookup"><span data-stu-id="3c2cb-108">The value STOP_UNMANAGED is only valid with interop debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c2cb-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3c2cb-109">Remarks</span></span>  
 <span data-ttu-id="3c2cb-110">Když ladicí program vyhledá kompilace za běhu (JIT), který nemá žádné odpovídající mapování na Microsoft (MSIL intermediate language), zastaví provádění Pokud byl nastaven příznak zadání typu nenamapovaný kódu; Krokování s transparentně pokračuje v, jinak hodnota.</span><span class="sxs-lookup"><span data-stu-id="3c2cb-110">When the debugger finds a just-in-time (JIT) compilation that has no corresponding mapping to Microsoft intermediate language (MSIL), it halts execution if the flag specifying that type of unmapped code has been set; otherwise, stepping transparently continues.</span></span>  
  
 <span data-ttu-id="3c2cb-111">Pokud ladicí program nepoužívá krokovač zadat metodu, pak jej nebude krok nutně přes nenamapovaný kódu.</span><span class="sxs-lookup"><span data-stu-id="3c2cb-111">If the debugger doesn't use a stepper to enter a method, then it won't necessarily step over unmapped code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c2cb-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3c2cb-112">Requirements</span></span>  
 <span data-ttu-id="3c2cb-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c2cb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c2cb-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3c2cb-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c2cb-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c2cb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c2cb-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c2cb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
