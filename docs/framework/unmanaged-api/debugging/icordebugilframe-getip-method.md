---
title: "ICorDebugILFrame::GetIP – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 79b18c6fe15e28b2cec07ef9dfaa06ee295ab42d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframegetip-method"></a><span data-ttu-id="e17a8-102">ICorDebugILFrame::GetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="e17a8-102">ICorDebugILFrame::GetIP Method</span></span>
<span data-ttu-id="e17a8-103">Získá hodnotu ukazatel instrukce a bitovou kombinaci hodnotu, která popisuje, jak byla získána hodnota ukazatele instrukcí.</span><span class="sxs-lookup"><span data-stu-id="e17a8-103">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e17a8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e17a8-104">Syntax</span></span>  
  
```  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,   
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e17a8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e17a8-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="e17a8-106">[out] Hodnota ukazatele instrukcí.</span><span class="sxs-lookup"><span data-stu-id="e17a8-106">[out] The value of the instruction pointer.</span></span>  
  
 `pMappingResult`  
 <span data-ttu-id="e17a8-107">[out] Ukazatel na bitová kombinace hodnot výčtu CorDebugMappingResult, které popisují, jak byla získána hodnota ukazatele instrukcí.</span><span class="sxs-lookup"><span data-stu-id="e17a8-107">[out] A pointer to a bitwise combination of the CorDebugMappingResult enumeration values that describe how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e17a8-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e17a8-108">Remarks</span></span>  
 <span data-ttu-id="e17a8-109">Ukazatel instrukce hodnotu rámce zásobníku odsazení kód funkce Microsoft (MSIL intermediate language).</span><span class="sxs-lookup"><span data-stu-id="e17a8-109">The value of the instruction pointer is the stack frame's offset into the function's Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="e17a8-110">Pokud rámce zásobníku je aktivní, tato adresa se další pokyny k provedení.</span><span class="sxs-lookup"><span data-stu-id="e17a8-110">If the stack frame is active, this address is the next instruction to execute.</span></span> <span data-ttu-id="e17a8-111">Pokud rámce zásobníku není aktivní, tato adresa se další pokyny k provedení při opětovné aktivaci rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="e17a8-111">If the stack frame is not active, this address is the next instruction to execute when the stack frame is reactivated.</span></span>  
  
 <span data-ttu-id="e17a8-112">Pokud je tento rámeček rámeček kompilované za běhu (JIT), hodnota ukazatele instrukce určí mapování zpětné z ukazatel na skutečné nativní instrukce, takže hodnota může být jen přibližné.</span><span class="sxs-lookup"><span data-stu-id="e17a8-112">If this frame is a just-in-time (JIT) compiled frame, the value of the instruction pointer will be determined by mapping backwards from the actual native instruction pointer, so the value may be only approximate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e17a8-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e17a8-113">Requirements</span></span>  
 <span data-ttu-id="e17a8-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e17a8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e17a8-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e17a8-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e17a8-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e17a8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e17a8-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e17a8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
