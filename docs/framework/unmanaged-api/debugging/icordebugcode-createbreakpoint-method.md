---
title: ICorDebugCode::CreateBreakpoint – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.CreateBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::CreateBreakpoint
helpviewer_keywords:
- ICorDebugCode::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 46842618-0fe4-480b-871c-82fba82d23d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1173091a5f2d8814747c93f827150afe39b8b309
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399107"
---
# <a name="icordebugcodecreatebreakpoint-method"></a><span data-ttu-id="23a7d-102">ICorDebugCode::CreateBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="23a7d-102">ICorDebugCode::CreateBreakpoint Method</span></span>
<span data-ttu-id="23a7d-103">Vytvoří zarážky v tomto segmentu kódu na zadaném posunu.</span><span class="sxs-lookup"><span data-stu-id="23a7d-103">Creates a breakpoint in this code segment at the specified offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23a7d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23a7d-104">Syntax</span></span>  
  
```  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="23a7d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="23a7d-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="23a7d-106">[v] Posun, pro kterou chcete vytvořit bod přerušení.</span><span class="sxs-lookup"><span data-stu-id="23a7d-106">[in] The offset at which to create the breakpoint.</span></span>  
  
 `ppBreakpoint`  
 <span data-ttu-id="23a7d-107">[out] Ukazatel na adresu "ICorDebugFunctionBreakpoint" objekt, který představuje bod přerušení.</span><span class="sxs-lookup"><span data-stu-id="23a7d-107">[out] A pointer to the address of an "ICorDebugFunctionBreakpoint" object that represents the breakpoint.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23a7d-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="23a7d-108">Remarks</span></span>  
 <span data-ttu-id="23a7d-109">Předtím, než je aktivní bod přerušení, musí být přidané na objekt procesu.</span><span class="sxs-lookup"><span data-stu-id="23a7d-109">Before the breakpoint is active, it must be added to the process object.</span></span>  
  
 <span data-ttu-id="23a7d-110">Pokud tento kód je kód Microsoft intermediate language (MSIL), a dojde v běhu (JIT)-kompilované, nativní verzi kód zarážce se použijí v kompilována kódu.</span><span class="sxs-lookup"><span data-stu-id="23a7d-110">If this code is Microsoft intermediate language (MSIL) code, and there is a just-in-time (JIT)-compiled, native version of the code, the breakpoint will be applied in the JIT-compiled code as well.</span></span> <span data-ttu-id="23a7d-111">(Stejná je hodnota true, pokud kód je kompilována později.)</span><span class="sxs-lookup"><span data-stu-id="23a7d-111">(The same is true if the code is JIT-compiled later.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23a7d-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="23a7d-112">Requirements</span></span>  
 <span data-ttu-id="23a7d-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23a7d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23a7d-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="23a7d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="23a7d-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23a7d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23a7d-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23a7d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23a7d-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="23a7d-117">See Also</span></span>  
 
