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
ms.openlocfilehash: fdd2151c4886959647de4f9e27a20a93ffc07429
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420050"
---
# <a name="icordebugfunction2getversionnumber-method"></a><span data-ttu-id="b206f-102">ICorDebugFunction2::GetVersionNumber – metoda</span><span class="sxs-lookup"><span data-stu-id="b206f-102">ICorDebugFunction2::GetVersionNumber Method</span></span>
<span data-ttu-id="b206f-103">Získá verzi aplikace upravit a pokračovat v této funkce.</span><span class="sxs-lookup"><span data-stu-id="b206f-103">Gets the Edit and Continue version of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b206f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b206f-104">Syntax</span></span>  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b206f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b206f-105">Parameters</span></span>  
 `pnVersion`  
 <span data-ttu-id="b206f-106">[out] Ukazatel na celé číslo, které je funkce, která je reprezentována tento objekt ICorDebugFunction2 číslo verze.</span><span class="sxs-lookup"><span data-stu-id="b206f-106">[out] A pointer to an integer that is the version number of the function that is represented by this ICorDebugFunction2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b206f-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b206f-107">Remarks</span></span>  
 <span data-ttu-id="b206f-108">Modul runtime uchovává informace o počtu úprav, které byly provedeny na každý modul během ladicí relace.</span><span class="sxs-lookup"><span data-stu-id="b206f-108">The runtime keeps track of the number of edits that have taken place to each module during a debug session.</span></span> <span data-ttu-id="b206f-109">Číslo verze funkce je jedním více než počet zavedena funkce upravit.</span><span class="sxs-lookup"><span data-stu-id="b206f-109">The version number of a function is one more than the number of the edit that introduced the function.</span></span> <span data-ttu-id="b206f-110">Funkce na původní verze je verze 1.</span><span class="sxs-lookup"><span data-stu-id="b206f-110">The function's original version is version 1.</span></span> <span data-ttu-id="b206f-111">Číslo je zvýšena pro modul pokaždé, když [icordebugmodule2::applychanges –](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) je volána v tomto modulu.</span><span class="sxs-lookup"><span data-stu-id="b206f-111">The number is incremented for a module every time [ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) is called on that module.</span></span> <span data-ttu-id="b206f-112">Proto pokud byl nahrazen tělo funkce ve volání první a třetí `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` může vrátit verze 1, 2 nebo 4 pro tuto funkci, ale verze 3.</span><span class="sxs-lookup"><span data-stu-id="b206f-112">Thus, if a function’s body was replaced in the first and third call to `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` may return version 1, 2, or 4 for that function, but not version 3.</span></span> <span data-ttu-id="b206f-113">(Této funkce by měla mít žádná verze 3.)</span><span class="sxs-lookup"><span data-stu-id="b206f-113">(That function would have no version 3.)</span></span>  
  
 <span data-ttu-id="b206f-114">Číslo verze je nezávisle sledovaný pro každý modul.</span><span class="sxs-lookup"><span data-stu-id="b206f-114">The version number is tracked separately for each module.</span></span> <span data-ttu-id="b206f-115">Ano Pokud provádíte čtyři úpravy v modulu 1 a žádná modulu 2, přidělí další úpravy v modulu 1 číslo verze 6 k všechny upravená funkce v modulu 1.</span><span class="sxs-lookup"><span data-stu-id="b206f-115">So, if you perform four edits on Module 1, and none on Module 2, your next edit on Module 1 will assign a version number of 6 to all the edited functions in Module 1.</span></span> <span data-ttu-id="b206f-116">Pokud stejný upravit úpravy 2 modulu, funkce v modulu 2 dostane číslo verze 2.</span><span class="sxs-lookup"><span data-stu-id="b206f-116">If the same edit touches Module 2, the functions in Module 2 will get a version number of 2.</span></span>  
  
 <span data-ttu-id="b206f-117">Číslo verze získat `GetVersionNumber` metoda může být nižší než získat [icordebugfunction::getcurrentversionnumber –](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md).</span><span class="sxs-lookup"><span data-stu-id="b206f-117">The version number obtained by the `GetVersionNumber` method may be lower than that obtained by [ICorDebugFunction::GetCurrentVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md).</span></span>  
  
 <span data-ttu-id="b206f-118">[Icordebugcode::getversionnumber –](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) metoda provádí stejné operace jako `ICorDebugFunction2::GetVersionNumber`.</span><span class="sxs-lookup"><span data-stu-id="b206f-118">The [ICorDebugCode::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) method performs the same operation as `ICorDebugFunction2::GetVersionNumber`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b206f-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b206f-119">Requirements</span></span>  
 <span data-ttu-id="b206f-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b206f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b206f-121">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b206f-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b206f-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b206f-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b206f-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b206f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
