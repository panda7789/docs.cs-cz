---
title: "ICorDebugStepper::SetUnmappedStopMask – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2fffd523caef6bba1b495f9b8a257f57bd8955af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a><span data-ttu-id="b90eb-102">ICorDebugStepper::SetUnmappedStopMask – metoda</span><span class="sxs-lookup"><span data-stu-id="b90eb-102">ICorDebugStepper::SetUnmappedStopMask Method</span></span>
<span data-ttu-id="b90eb-103">Nastaví hodnotu, která určuje typ nenamapovaný kódu, ve kterém se zastaví provádění.</span><span class="sxs-lookup"><span data-stu-id="b90eb-103">Sets a value that specifies the type of unmapped code in which execution will halt.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b90eb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b90eb-104">Syntax</span></span>  
  
```  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b90eb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b90eb-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="b90eb-106">[v] Hodnota CorDebugUnmappedStop – výčet, který určuje typ nenamapovaný kódu, ve kterém bude zastavení ladicího programu provádění.</span><span class="sxs-lookup"><span data-stu-id="b90eb-106">[in] A value of the CorDebugUnmappedStop enumeration that specifies the type of unmapped code in which the debugger will halt execution.</span></span>  
  
 <span data-ttu-id="b90eb-107">Výchozí hodnota je STOP_OTHER_UNMAPPED.</span><span class="sxs-lookup"><span data-stu-id="b90eb-107">The default value is STOP_OTHER_UNMAPPED.</span></span> <span data-ttu-id="b90eb-108">Hodnota STOP_UNMANAGED je platný pouze s spolupráce ladění.</span><span class="sxs-lookup"><span data-stu-id="b90eb-108">The value STOP_UNMANAGED is only valid with interop debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b90eb-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b90eb-109">Remarks</span></span>  
 <span data-ttu-id="b90eb-110">Když ladicí program vyhledá kompilace za běhu (JIT), který nemá žádné odpovídající mapování na Microsoft (MSIL intermediate language), zastaví provádění Pokud byl nastaven příznak zadání typu nenamapovaný kódu; Krokování s transparentně pokračuje v, jinak hodnota.</span><span class="sxs-lookup"><span data-stu-id="b90eb-110">When the debugger finds a just-in-time (JIT) compilation that has no corresponding mapping to Microsoft intermediate language (MSIL), it halts execution if the flag specifying that type of unmapped code has been set; otherwise, stepping transparently continues.</span></span>  
  
 <span data-ttu-id="b90eb-111">Pokud ladicí program nepoužívá krokovač zadat metodu, pak jej nebude krok nutně přes nenamapovaný kódu.</span><span class="sxs-lookup"><span data-stu-id="b90eb-111">If the debugger doesn't use a stepper to enter a method, then it won't necessarily step over unmapped code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b90eb-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b90eb-112">Requirements</span></span>  
 <span data-ttu-id="b90eb-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b90eb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b90eb-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b90eb-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b90eb-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b90eb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b90eb-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b90eb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
