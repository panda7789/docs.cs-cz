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
ms.openlocfilehash: d193f9aa4d051baa73944545d28a455495aeda40
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59185767"
---
# <a name="icordebugcodecreatebreakpoint-method"></a><span data-ttu-id="1d9c6-102">ICorDebugCode::CreateBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="1d9c6-102">ICorDebugCode::CreateBreakpoint Method</span></span>
<span data-ttu-id="1d9c6-103">Vytvoří zarážku v tomto segmentu kódu v zadaném posunu.</span><span class="sxs-lookup"><span data-stu-id="1d9c6-103">Creates a breakpoint in this code segment at the specified offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d9c6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d9c6-104">Syntax</span></span>  
  
```  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d9c6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1d9c6-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="1d9c6-106">[in] Posun, na kterém chcete vytvořit zarážku.</span><span class="sxs-lookup"><span data-stu-id="1d9c6-106">[in] The offset at which to create the breakpoint.</span></span>  
  
 `ppBreakpoint`  
 <span data-ttu-id="1d9c6-107">[out] Ukazatel na adresu objektu "icordebugfunctionbreakpoint –", který představuje zarážku.</span><span class="sxs-lookup"><span data-stu-id="1d9c6-107">[out] A pointer to the address of an "ICorDebugFunctionBreakpoint" object that represents the breakpoint.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d9c6-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1d9c6-108">Remarks</span></span>  
 <span data-ttu-id="1d9c6-109">Předtím, než je zarážky aktivní, je nutné přidat do objektu process.</span><span class="sxs-lookup"><span data-stu-id="1d9c6-109">Before the breakpoint is active, it must be added to the process object.</span></span>  
  
 <span data-ttu-id="1d9c6-110">Pokud tento kód je kód Microsoft intermediate language (MSIL) a je just-in-time (JIT)-kompilované, nativní verzi kódu, zarážka se použijí v kompilaci JIT kódu.</span><span class="sxs-lookup"><span data-stu-id="1d9c6-110">If this code is Microsoft intermediate language (MSIL) code, and there is a just-in-time (JIT)-compiled, native version of the code, the breakpoint will be applied in the JIT-compiled code as well.</span></span> <span data-ttu-id="1d9c6-111">(Stejný je hodnota true, pokud kód je zkompilován JIT Kompilátorem později.)</span><span class="sxs-lookup"><span data-stu-id="1d9c6-111">(The same is true if the code is JIT-compiled later.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d9c6-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1d9c6-112">Requirements</span></span>  
 <span data-ttu-id="1d9c6-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d9c6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d9c6-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1d9c6-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d9c6-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d9c6-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="1d9c6-116">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="1d9c6-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1d9c6-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d9c6-117">See also</span></span>
