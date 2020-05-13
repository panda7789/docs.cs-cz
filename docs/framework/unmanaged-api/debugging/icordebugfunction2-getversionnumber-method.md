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
ms.openlocfilehash: f47263872b1baf1038a5fa9816c96e3e2569e705
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213215"
---
# <a name="icordebugfunction2getversionnumber-method"></a><span data-ttu-id="da23e-102">ICorDebugFunction2::GetVersionNumber – metoda</span><span class="sxs-lookup"><span data-stu-id="da23e-102">ICorDebugFunction2::GetVersionNumber Method</span></span>
<span data-ttu-id="da23e-103">Získá verzi této funkce pro úpravu a pokračování.</span><span class="sxs-lookup"><span data-stu-id="da23e-103">Gets the Edit and Continue version of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da23e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da23e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da23e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="da23e-105">Parameters</span></span>  
 `pnVersion`  
 <span data-ttu-id="da23e-106">mimo Ukazatel na celé číslo, které je číslem verze funkce reprezentované tímto objektem ICorDebugFunction2.</span><span class="sxs-lookup"><span data-stu-id="da23e-106">[out] A pointer to an integer that is the version number of the function that is represented by this ICorDebugFunction2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da23e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="da23e-107">Remarks</span></span>  
 <span data-ttu-id="da23e-108">Modul runtime uchovává přehled o počtu úprav, které byly provedeny v jednotlivých modulech během relace ladění.</span><span class="sxs-lookup"><span data-stu-id="da23e-108">The runtime keeps track of the number of edits that have taken place to each module during a debug session.</span></span> <span data-ttu-id="da23e-109">Číslo verze funkce je o jednu vyšší, než je počet úprav, které tuto funkci zavedly.</span><span class="sxs-lookup"><span data-stu-id="da23e-109">The version number of a function is one more than the number of the edit that introduced the function.</span></span> <span data-ttu-id="da23e-110">Původní verze funkce je verze 1.</span><span class="sxs-lookup"><span data-stu-id="da23e-110">The function's original version is version 1.</span></span> <span data-ttu-id="da23e-111">Číslo se zvyšuje pro modul pokaždé, když [ICorDebugModule2:: ApplyChanges –](icordebugmodule2-applychanges-method.md) je v tomto modulu volán.</span><span class="sxs-lookup"><span data-stu-id="da23e-111">The number is incremented for a module every time [ICorDebugModule2::ApplyChanges](icordebugmodule2-applychanges-method.md) is called on that module.</span></span> <span data-ttu-id="da23e-112">Proto, pokud byl tělo funkce nahrazeno prvním a třetím voláním `ICorDebugModule2::ApplyChanges` , `GetVersionNumber` může pro tuto funkci vracet verze 1, 2 nebo 4, ale ne verze 3.</span><span class="sxs-lookup"><span data-stu-id="da23e-112">Thus, if a function’s body was replaced in the first and third call to `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` may return version 1, 2, or 4 for that function, but not version 3.</span></span> <span data-ttu-id="da23e-113">(Tato funkce by nemusela mít verzi 3.)</span><span class="sxs-lookup"><span data-stu-id="da23e-113">(That function would have no version 3.)</span></span>  
  
 <span data-ttu-id="da23e-114">Číslo verze se sleduje samostatně pro každý modul.</span><span class="sxs-lookup"><span data-stu-id="da23e-114">The version number is tracked separately for each module.</span></span> <span data-ttu-id="da23e-115">Pokud tedy v modulu 1 provedete čtyři úpravy a v modulu 2 nejsou žádné, vaše další úprava v modulu 1 přiřadí ke všem upraveným funkcím v modulu 1 číslo verze 6.</span><span class="sxs-lookup"><span data-stu-id="da23e-115">So, if you perform four edits on Module 1, and none on Module 2, your next edit on Module 1 will assign a version number of 6 to all the edited functions in Module 1.</span></span> <span data-ttu-id="da23e-116">Pokud se ve stejné úpravě dotkne modul 2, funkce v modulu 2 obdrží číslo verze 2.</span><span class="sxs-lookup"><span data-stu-id="da23e-116">If the same edit touches Module 2, the functions in Module 2 will get a version number of 2.</span></span>  
  
 <span data-ttu-id="da23e-117">Číslo verze získané `GetVersionNumber` metodou může být nižší než hodnota získaná pomocí [ICorDebugFunction:: GetCurrentVersionNumber –](icordebugfunction-getcurrentversionnumber-method.md).</span><span class="sxs-lookup"><span data-stu-id="da23e-117">The version number obtained by the `GetVersionNumber` method may be lower than that obtained by [ICorDebugFunction::GetCurrentVersionNumber](icordebugfunction-getcurrentversionnumber-method.md).</span></span>  
  
 <span data-ttu-id="da23e-118">Metoda [ICorDebugCode:: getčíslo_verze](icordebugcode-getversionnumber-method.md) provádí stejnou operaci jako `ICorDebugFunction2::GetVersionNumber` .</span><span class="sxs-lookup"><span data-stu-id="da23e-118">The [ICorDebugCode::GetVersionNumber](icordebugcode-getversionnumber-method.md) method performs the same operation as `ICorDebugFunction2::GetVersionNumber`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da23e-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="da23e-119">Requirements</span></span>  
 <span data-ttu-id="da23e-120">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da23e-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da23e-121">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="da23e-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da23e-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="da23e-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da23e-123">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da23e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
