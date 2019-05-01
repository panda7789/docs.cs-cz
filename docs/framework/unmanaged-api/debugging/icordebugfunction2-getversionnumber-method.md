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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6cc9c2af62184c83857b82445941f6087a05c2c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995603"
---
# <a name="icordebugfunction2getversionnumber-method"></a><span data-ttu-id="f015c-102">ICorDebugFunction2::GetVersionNumber – metoda</span><span class="sxs-lookup"><span data-stu-id="f015c-102">ICorDebugFunction2::GetVersionNumber Method</span></span>
<span data-ttu-id="f015c-103">Získá verzi této funkce upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="f015c-103">Gets the Edit and Continue version of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f015c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f015c-104">Syntax</span></span>  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f015c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f015c-105">Parameters</span></span>  
 `pnVersion`  
 <span data-ttu-id="f015c-106">[out] Ukazatel na celé číslo, které je číslo verze, která je reprezentována tímto objektem icordebugfunction2 – funkce</span><span class="sxs-lookup"><span data-stu-id="f015c-106">[out] A pointer to an integer that is the version number of the function that is represented by this ICorDebugFunction2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f015c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f015c-107">Remarks</span></span>  
 <span data-ttu-id="f015c-108">Modul runtime uchovává informace o počtu úpravy, které byly provedeny pro každý modul během relace ladění.</span><span class="sxs-lookup"><span data-stu-id="f015c-108">The runtime keeps track of the number of edits that have taken place to each module during a debug session.</span></span> <span data-ttu-id="f015c-109">Číslo verze funkce je jeden vyšší než počet úpravy funkce zavedena.</span><span class="sxs-lookup"><span data-stu-id="f015c-109">The version number of a function is one more than the number of the edit that introduced the function.</span></span> <span data-ttu-id="f015c-110">Původní verze této funkce je verze 1.</span><span class="sxs-lookup"><span data-stu-id="f015c-110">The function's original version is version 1.</span></span> <span data-ttu-id="f015c-111">Počet se zvýší pro modul pokaždé, když [icordebugmodule2::applychanges –](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) je volána v tomto modulu.</span><span class="sxs-lookup"><span data-stu-id="f015c-111">The number is incremented for a module every time [ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) is called on that module.</span></span> <span data-ttu-id="f015c-112">Proto pokud tělo funkce jsou nahrazené v první a třetí volání `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` může vrátit verze 1, 2 nebo 4 pro tuto funkci, ale ne verzi 3.</span><span class="sxs-lookup"><span data-stu-id="f015c-112">Thus, if a function’s body was replaced in the first and third call to `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` may return version 1, 2, or 4 for that function, but not version 3.</span></span> <span data-ttu-id="f015c-113">(Tato funkce nemá žádné verze 3.)</span><span class="sxs-lookup"><span data-stu-id="f015c-113">(That function would have no version 3.)</span></span>  
  
 <span data-ttu-id="f015c-114">Číslo verze je sledována samostatně pro každý modul.</span><span class="sxs-lookup"><span data-stu-id="f015c-114">The version number is tracked separately for each module.</span></span> <span data-ttu-id="f015c-115">Proto pokud provádění čtyři úprav v modulu 1 a žádné v modulu 2, další úpravy na modulu 1 přiřadí číslo verze 6 všechny upravené funkce v modulu 1.</span><span class="sxs-lookup"><span data-stu-id="f015c-115">So, if you perform four edits on Module 1, and none on Module 2, your next edit on Module 1 will assign a version number of 6 to all the edited functions in Module 1.</span></span> <span data-ttu-id="f015c-116">Pokud stejný upravit dnešní 2 modulu, funkce v modulu 2 se číslo verze 2.</span><span class="sxs-lookup"><span data-stu-id="f015c-116">If the same edit touches Module 2, the functions in Module 2 will get a version number of 2.</span></span>  
  
 <span data-ttu-id="f015c-117">Získá číslo verze `GetVersionNumber` metoda může být nižší než, která získá [icordebugfunction::getcurrentversionnumber –](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md).</span><span class="sxs-lookup"><span data-stu-id="f015c-117">The version number obtained by the `GetVersionNumber` method may be lower than that obtained by [ICorDebugFunction::GetCurrentVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md).</span></span>  
  
 <span data-ttu-id="f015c-118">[Icordebugcode::getversionnumber –](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) metoda provede stejné operace jako `ICorDebugFunction2::GetVersionNumber`.</span><span class="sxs-lookup"><span data-stu-id="f015c-118">The [ICorDebugCode::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) method performs the same operation as `ICorDebugFunction2::GetVersionNumber`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f015c-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f015c-119">Requirements</span></span>  
 <span data-ttu-id="f015c-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f015c-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f015c-121">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f015c-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f015c-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f015c-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f015c-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f015c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
