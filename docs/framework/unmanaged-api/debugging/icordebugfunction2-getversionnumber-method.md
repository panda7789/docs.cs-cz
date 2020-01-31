---
title: ICorDebugFunction2::GetVersionNumber – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetVersionNumber
helpviewer_keywords:
- ICorDebugFunction2::GetVersionNumber method [.NET Framework debugging]
- GetVersionNumber method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: e3a1ce48-9bb9-4ed6-a5fe-5e1819a6333f
topic_type:
- apiref
ms.openlocfilehash: d85885d750f3c98e46b3e44418564da18850d3ec
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794490"
---
# <a name="icordebugfunction2getversionnumber-method"></a><span data-ttu-id="2c7a5-102">ICorDebugFunction2::GetVersionNumber – metoda</span><span class="sxs-lookup"><span data-stu-id="2c7a5-102">ICorDebugFunction2::GetVersionNumber Method</span></span>
<span data-ttu-id="2c7a5-103">Získá verzi této funkce pro úpravu a pokračování.</span><span class="sxs-lookup"><span data-stu-id="2c7a5-103">Gets the Edit and Continue version of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c7a5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c7a5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c7a5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2c7a5-105">Parameters</span></span>  
 `pnVersion`  
 <span data-ttu-id="2c7a5-106">mimo Ukazatel na celé číslo, které je číslem verze funkce reprezentované tímto objektem ICorDebugFunction2.</span><span class="sxs-lookup"><span data-stu-id="2c7a5-106">[out] A pointer to an integer that is the version number of the function that is represented by this ICorDebugFunction2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c7a5-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2c7a5-107">Remarks</span></span>  
 <span data-ttu-id="2c7a5-108">Modul runtime uchovává přehled o počtu úprav, které byly provedeny v jednotlivých modulech během relace ladění.</span><span class="sxs-lookup"><span data-stu-id="2c7a5-108">The runtime keeps track of the number of edits that have taken place to each module during a debug session.</span></span> <span data-ttu-id="2c7a5-109">Číslo verze funkce je o jednu vyšší, než je počet úprav, které tuto funkci zavedly.</span><span class="sxs-lookup"><span data-stu-id="2c7a5-109">The version number of a function is one more than the number of the edit that introduced the function.</span></span> <span data-ttu-id="2c7a5-110">Původní verze funkce je verze 1.</span><span class="sxs-lookup"><span data-stu-id="2c7a5-110">The function's original version is version 1.</span></span> <span data-ttu-id="2c7a5-111">Číslo se zvyšuje pro modul pokaždé, když [ICorDebugModule2:: ApplyChanges –](icordebugmodule2-applychanges-method.md) je v tomto modulu volán.</span><span class="sxs-lookup"><span data-stu-id="2c7a5-111">The number is incremented for a module every time [ICorDebugModule2::ApplyChanges](icordebugmodule2-applychanges-method.md) is called on that module.</span></span> <span data-ttu-id="2c7a5-112">Proto pokud byl tělo funkce nahrazeno prvním a třetím voláním `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` může pro tuto funkci vracet verze 1, 2 nebo 4, ale ne verze 3.</span><span class="sxs-lookup"><span data-stu-id="2c7a5-112">Thus, if a function’s body was replaced in the first and third call to `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` may return version 1, 2, or 4 for that function, but not version 3.</span></span> <span data-ttu-id="2c7a5-113">(Tato funkce by nemusela mít verzi 3.)</span><span class="sxs-lookup"><span data-stu-id="2c7a5-113">(That function would have no version 3.)</span></span>  
  
 <span data-ttu-id="2c7a5-114">Číslo verze se sleduje samostatně pro každý modul.</span><span class="sxs-lookup"><span data-stu-id="2c7a5-114">The version number is tracked separately for each module.</span></span> <span data-ttu-id="2c7a5-115">Pokud tedy v modulu 1 provedete čtyři úpravy a v modulu 2 nejsou žádné, vaše další úprava v modulu 1 přiřadí ke všem upraveným funkcím v modulu 1 číslo verze 6.</span><span class="sxs-lookup"><span data-stu-id="2c7a5-115">So, if you perform four edits on Module 1, and none on Module 2, your next edit on Module 1 will assign a version number of 6 to all the edited functions in Module 1.</span></span> <span data-ttu-id="2c7a5-116">Pokud se ve stejné úpravě dotkne modul 2, funkce v modulu 2 obdrží číslo verze 2.</span><span class="sxs-lookup"><span data-stu-id="2c7a5-116">If the same edit touches Module 2, the functions in Module 2 will get a version number of 2.</span></span>  
  
 <span data-ttu-id="2c7a5-117">Číslo verze získané metodou `GetVersionNumber` může být nižší než hodnota získaná pomocí [ICorDebugFunction:: GetCurrentVersionNumber –](icordebugfunction-getcurrentversionnumber-method.md).</span><span class="sxs-lookup"><span data-stu-id="2c7a5-117">The version number obtained by the `GetVersionNumber` method may be lower than that obtained by [ICorDebugFunction::GetCurrentVersionNumber](icordebugfunction-getcurrentversionnumber-method.md).</span></span>  
  
 <span data-ttu-id="2c7a5-118">Metoda [ICorDebugCode:: getčíslo_verze](icordebugcode-getversionnumber-method.md) provede stejnou operaci jako `ICorDebugFunction2::GetVersionNumber`.</span><span class="sxs-lookup"><span data-stu-id="2c7a5-118">The [ICorDebugCode::GetVersionNumber](icordebugcode-getversionnumber-method.md) method performs the same operation as `ICorDebugFunction2::GetVersionNumber`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c7a5-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2c7a5-119">Requirements</span></span>  
 <span data-ttu-id="2c7a5-120">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c7a5-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c7a5-121">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2c7a5-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c7a5-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2c7a5-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c7a5-123">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c7a5-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
