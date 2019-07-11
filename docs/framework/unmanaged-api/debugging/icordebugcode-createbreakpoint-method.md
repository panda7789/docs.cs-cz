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
ms.openlocfilehash: 07f8be1a1831bc00eea3cfb659b46b67b6a78711
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747734"
---
# <a name="icordebugcodecreatebreakpoint-method"></a><span data-ttu-id="8c572-102">ICorDebugCode::CreateBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="8c572-102">ICorDebugCode::CreateBreakpoint Method</span></span>
<span data-ttu-id="8c572-103">Vytvoří zarážku v tomto segmentu kódu v zadaném posunu.</span><span class="sxs-lookup"><span data-stu-id="8c572-103">Creates a breakpoint in this code segment at the specified offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c572-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c572-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c572-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8c572-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="8c572-106">[in] Posun, na kterém chcete vytvořit zarážku.</span><span class="sxs-lookup"><span data-stu-id="8c572-106">[in] The offset at which to create the breakpoint.</span></span>  
  
 `ppBreakpoint`  
 <span data-ttu-id="8c572-107">[out] Ukazatel na adresu objektu "icordebugfunctionbreakpoint –", který představuje zarážku.</span><span class="sxs-lookup"><span data-stu-id="8c572-107">[out] A pointer to the address of an "ICorDebugFunctionBreakpoint" object that represents the breakpoint.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c572-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8c572-108">Remarks</span></span>  
 <span data-ttu-id="8c572-109">Předtím, než je zarážky aktivní, je nutné přidat do objektu process.</span><span class="sxs-lookup"><span data-stu-id="8c572-109">Before the breakpoint is active, it must be added to the process object.</span></span>  
  
 <span data-ttu-id="8c572-110">Pokud tento kód je kód Microsoft intermediate language (MSIL) a je just-in-time (JIT)-kompilované, nativní verzi kódu, zarážka se použijí v kompilaci JIT kódu.</span><span class="sxs-lookup"><span data-stu-id="8c572-110">If this code is Microsoft intermediate language (MSIL) code, and there is a just-in-time (JIT)-compiled, native version of the code, the breakpoint will be applied in the JIT-compiled code as well.</span></span> <span data-ttu-id="8c572-111">(Stejný je hodnota true, pokud kód je zkompilován JIT Kompilátorem později.)</span><span class="sxs-lookup"><span data-stu-id="8c572-111">(The same is true if the code is JIT-compiled later.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c572-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8c572-112">Requirements</span></span>  
 <span data-ttu-id="8c572-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c572-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c572-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8c572-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c572-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c572-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c572-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c572-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c572-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c572-117">See also</span></span>
