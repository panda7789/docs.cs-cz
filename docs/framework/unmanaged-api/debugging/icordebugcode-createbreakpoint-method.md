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
ms.openlocfilehash: 1ec7d615b99ac301948d7ea25318115713ce06ea
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700846"
---
# <a name="icordebugcodecreatebreakpoint-method"></a><span data-ttu-id="a85e8-102">ICorDebugCode::CreateBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="a85e8-102">ICorDebugCode::CreateBreakpoint Method</span></span>
<span data-ttu-id="a85e8-103">Vytvoří zarážku v tomto segmentu kódu na zadaném posunu.</span><span class="sxs-lookup"><span data-stu-id="a85e8-103">Creates a breakpoint in this code segment at the specified offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a85e8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a85e8-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a85e8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a85e8-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="a85e8-106">pro Posun, ve kterém má být vytvořena zarážka.</span><span class="sxs-lookup"><span data-stu-id="a85e8-106">[in] The offset at which to create the breakpoint.</span></span>  
  
 `ppBreakpoint`  
 <span data-ttu-id="a85e8-107">mimo Ukazatel na adresu objektu "ICorDebugFunctionBreakpoint", který představuje zarážku.</span><span class="sxs-lookup"><span data-stu-id="a85e8-107">[out] A pointer to the address of an "ICorDebugFunctionBreakpoint" object that represents the breakpoint.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a85e8-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a85e8-108">Remarks</span></span>  
 <span data-ttu-id="a85e8-109">Předtím, než je zarážka aktivní, je nutné ji přidat do objektu procesu.</span><span class="sxs-lookup"><span data-stu-id="a85e8-109">Before the breakpoint is active, it must be added to the process object.</span></span>  
  
 <span data-ttu-id="a85e8-110">Pokud je tento kód kódem jazyka MSIL (Microsoft Intermediate Language) a existuje nativní verze kódu kompilována za běhu (JIT), zarážka bude použita také v kódu kompilovaném JIT.</span><span class="sxs-lookup"><span data-stu-id="a85e8-110">If this code is Microsoft intermediate language (MSIL) code, and there is a just-in-time (JIT)-compiled, native version of the code, the breakpoint will be applied in the JIT-compiled code as well.</span></span> <span data-ttu-id="a85e8-111">(Totéž platí, pokud je kód zkompilován kompilátorem JIT později.)</span><span class="sxs-lookup"><span data-stu-id="a85e8-111">(The same is true if the code is JIT-compiled later.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a85e8-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a85e8-112">Requirements</span></span>  
 <span data-ttu-id="a85e8-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a85e8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a85e8-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a85e8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a85e8-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a85e8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a85e8-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a85e8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
