---
title: ICorDebugILFrame::GetIP – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::GetIP method [.NET Framework debugging]
ms.assetid: 18217ba1-1776-4297-a3b9-f77e64b0fead
topic_type:
- apiref
ms.openlocfilehash: f30516a8f59b90de9b4c052d92a8c88575ace3c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178828"
---
# <a name="icordebugilframegetip-method"></a><span data-ttu-id="66a16-102">ICorDebugILFrame::GetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="66a16-102">ICorDebugILFrame::GetIP Method</span></span>
<span data-ttu-id="66a16-103">Získá hodnotu ukazatele instrukce a bitové kombinace hodnotu, která popisuje, jak byla získána hodnota ukazatele instrukce.</span><span class="sxs-lookup"><span data-stu-id="66a16-103">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66a16-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66a16-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66a16-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="66a16-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="66a16-106">[out] Hodnota ukazatele instrukce.</span><span class="sxs-lookup"><span data-stu-id="66a16-106">[out] The value of the instruction pointer.</span></span>  
  
 `pMappingResult`  
 <span data-ttu-id="66a16-107">[out] Ukazatel na bitovou kombinaci hodnot výčtu CorDebugMappingResult, které popisují, jak byla získána hodnota ukazatele instrukce.</span><span class="sxs-lookup"><span data-stu-id="66a16-107">[out] A pointer to a bitwise combination of the CorDebugMappingResult enumeration values that describe how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66a16-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="66a16-108">Remarks</span></span>  
 <span data-ttu-id="66a16-109">Hodnota ukazatele instrukce je posun rámce zásobníku do kódu zprostředkujícího jazyka Microsoft (MSIL).</span><span class="sxs-lookup"><span data-stu-id="66a16-109">The value of the instruction pointer is the stack frame's offset into the function's Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="66a16-110">Pokud je aktivní rámec zásobníku, tato adresa je další instrukce ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="66a16-110">If the stack frame is active, this address is the next instruction to execute.</span></span> <span data-ttu-id="66a16-111">Pokud rámec zásobníku není aktivní, tato adresa je další instrukce provést při opětovné aktivaci rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="66a16-111">If the stack frame is not active, this address is the next instruction to execute when the stack frame is reactivated.</span></span>  
  
 <span data-ttu-id="66a16-112">Pokud tento rámec je kompilovaný rámec just-in-time (JIT), hodnota ukazatele instrukce bude určena mapováním zpět od skutečného ukazatele nativní instrukce, takže hodnota může být pouze přibližná.</span><span class="sxs-lookup"><span data-stu-id="66a16-112">If this frame is a just-in-time (JIT) compiled frame, the value of the instruction pointer will be determined by mapping backwards from the actual native instruction pointer, so the value may be only approximate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66a16-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66a16-113">Requirements</span></span>  
 <span data-ttu-id="66a16-114">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66a16-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66a16-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="66a16-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66a16-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66a16-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66a16-117">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66a16-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
