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
ms.openlocfilehash: ef458fda8e8b7e75f92a4b3c06eabec106180d23
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379250"
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a><span data-ttu-id="ad078-102">ICorDebugStepper::SetUnmappedStopMask – metoda</span><span class="sxs-lookup"><span data-stu-id="ad078-102">ICorDebugStepper::SetUnmappedStopMask Method</span></span>
<span data-ttu-id="ad078-103">Nastaví hodnotu, která určuje typ nemapovaného kódu, ve kterém se spuštění zastaví.</span><span class="sxs-lookup"><span data-stu-id="ad078-103">Sets a value that specifies the type of unmapped code in which execution will halt.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad078-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad078-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad078-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad078-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="ad078-106">pro Hodnota výčtu CorDebugUnmappedStop –, která určuje typ nemapovaného kódu, ve kterém ladicí program zastaví provádění.</span><span class="sxs-lookup"><span data-stu-id="ad078-106">[in] A value of the CorDebugUnmappedStop enumeration that specifies the type of unmapped code in which the debugger will halt execution.</span></span>  
  
 <span data-ttu-id="ad078-107">Výchozí hodnota je STOP_OTHER_UNMAPPED.</span><span class="sxs-lookup"><span data-stu-id="ad078-107">The default value is STOP_OTHER_UNMAPPED.</span></span> <span data-ttu-id="ad078-108">Hodnota STOP_UNMANAGED je platná pouze s laděním spolupráce.</span><span class="sxs-lookup"><span data-stu-id="ad078-108">The value STOP_UNMANAGED is only valid with interop debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad078-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ad078-109">Remarks</span></span>  
 <span data-ttu-id="ad078-110">Když ladicí program najde kompilaci za běhu (JIT), která nemá žádné odpovídající mapování na jazyk MSIL (Microsoft Intermediate Language), zastaví provádění, pokud byl nastaven příznak určující tento typ nemapovaného kódu; v opačném případě pokračuje krokování transparentně.</span><span class="sxs-lookup"><span data-stu-id="ad078-110">When the debugger finds a just-in-time (JIT) compilation that has no corresponding mapping to Microsoft intermediate language (MSIL), it halts execution if the flag specifying that type of unmapped code has been set; otherwise, stepping transparently continues.</span></span>  
  
 <span data-ttu-id="ad078-111">Pokud ladicí program nepoužívá stepper k zadání metody, pak nebude nutně Krokovat s nemapovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="ad078-111">If the debugger doesn't use a stepper to enter a method, then it won't necessarily step over unmapped code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad078-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ad078-112">Requirements</span></span>  
 <span data-ttu-id="ad078-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad078-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad078-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ad078-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad078-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ad078-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad078-116">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad078-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
