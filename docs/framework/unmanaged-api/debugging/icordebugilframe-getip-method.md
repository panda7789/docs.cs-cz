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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a7b8985e7580282d0e38205f9b1d6078f86cee6
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479763"
---
# <a name="icordebugilframegetip-method"></a><span data-ttu-id="7f6a4-102">ICorDebugILFrame::GetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="7f6a4-102">ICorDebugILFrame::GetIP Method</span></span>
<span data-ttu-id="7f6a4-103">Získá hodnotu ukazatele na instrukci a bitová kombinace hodnotu, která popisuje, jak byla získána hodnota ukazatele na instrukci.</span><span class="sxs-lookup"><span data-stu-id="7f6a4-103">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f6a4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f6a4-104">Syntax</span></span>  
  
```  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,   
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f6a4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f6a4-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="7f6a4-106">[out] Hodnota ukazatele na instrukci.</span><span class="sxs-lookup"><span data-stu-id="7f6a4-106">[out] The value of the instruction pointer.</span></span>  
  
 `pMappingResult`  
 <span data-ttu-id="7f6a4-107">[out] Ukazatel na bitová kombinace hodnot výčtu cordebugmappingresult –, které popisují, jak byla získána hodnota ukazatele na instrukci.</span><span class="sxs-lookup"><span data-stu-id="7f6a4-107">[out] A pointer to a bitwise combination of the CorDebugMappingResult enumeration values that describe how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f6a4-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7f6a4-108">Remarks</span></span>  
 <span data-ttu-id="7f6a4-109">Hodnota ukazatele na instrukci je odsazení rámce zásobníku do kód funkce Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="7f6a4-109">The value of the instruction pointer is the stack frame's offset into the function's Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="7f6a4-110">Pokud je aktivní rámec zásobníku, tato adresa je další instrukci k provedení.</span><span class="sxs-lookup"><span data-stu-id="7f6a4-110">If the stack frame is active, this address is the next instruction to execute.</span></span> <span data-ttu-id="7f6a4-111">Pokud není aktivní rámec zásobníku, tato adresa je další instrukci má provést, když se znovu aktivuje rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="7f6a4-111">If the stack frame is not active, this address is the next instruction to execute when the stack frame is reactivated.</span></span>  
  
 <span data-ttu-id="7f6a4-112">Pokud je tento rámeček blok kompilované just-in-time (JIT), hodnota ukazatele na instrukci určí zpětné mapování z ukazatele na instrukci skutečná nativní, takže hodnota může být pouze přibližná.</span><span class="sxs-lookup"><span data-stu-id="7f6a4-112">If this frame is a just-in-time (JIT) compiled frame, the value of the instruction pointer will be determined by mapping backwards from the actual native instruction pointer, so the value may be only approximate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f6a4-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7f6a4-113">Requirements</span></span>  
 <span data-ttu-id="7f6a4-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f6a4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f6a4-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7f6a4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7f6a4-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f6a4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f6a4-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f6a4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
