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
ms.openlocfilehash: 3890cb4236f113bc6efc23bfb606d19a525ec234
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210264"
---
# <a name="icordebugilframegetip-method"></a><span data-ttu-id="e412b-102">ICorDebugILFrame::GetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="e412b-102">ICorDebugILFrame::GetIP Method</span></span>
<span data-ttu-id="e412b-103">Získá hodnotu ukazatele na instrukci a bitovou kombinaci hodnoty, která popisuje, jak byla získána hodnota ukazatele na instrukci.</span><span class="sxs-lookup"><span data-stu-id="e412b-103">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e412b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e412b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e412b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e412b-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="e412b-106">mimo Hodnota ukazatele na instrukci.</span><span class="sxs-lookup"><span data-stu-id="e412b-106">[out] The value of the instruction pointer.</span></span>  
  
 `pMappingResult`  
 <span data-ttu-id="e412b-107">mimo Ukazatel na bitovou kombinaci hodnot výčtu CorDebugMappingResult –, které popisují, jak byla získána hodnota ukazatele na instrukci.</span><span class="sxs-lookup"><span data-stu-id="e412b-107">[out] A pointer to a bitwise combination of the CorDebugMappingResult enumeration values that describe how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e412b-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e412b-108">Remarks</span></span>  
 <span data-ttu-id="e412b-109">Hodnota ukazatele na instrukci je posun rámce zásobníku do kódu jazyka MSIL (Microsoft Intermediate Language) funkce.</span><span class="sxs-lookup"><span data-stu-id="e412b-109">The value of the instruction pointer is the stack frame's offset into the function's Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="e412b-110">Pokud je rámec zásobníku aktivní, je tato adresa další instrukcí, která se má provést.</span><span class="sxs-lookup"><span data-stu-id="e412b-110">If the stack frame is active, this address is the next instruction to execute.</span></span> <span data-ttu-id="e412b-111">Pokud není rámec zásobníku aktivní, jedná se o další instrukci, která se má provést, když se rámec zásobníku znovu aktivuje.</span><span class="sxs-lookup"><span data-stu-id="e412b-111">If the stack frame is not active, this address is the next instruction to execute when the stack frame is reactivated.</span></span>  
  
 <span data-ttu-id="e412b-112">Pokud je tento rámec kompilovaným snímkem just-in-time (JIT), hodnota ukazatele na instrukci bude určena mapováním zpět od skutečného nativního ukazatele instrukcí, takže hodnota může být pouze přibližná.</span><span class="sxs-lookup"><span data-stu-id="e412b-112">If this frame is a just-in-time (JIT) compiled frame, the value of the instruction pointer will be determined by mapping backwards from the actual native instruction pointer, so the value may be only approximate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e412b-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e412b-113">Requirements</span></span>  
 <span data-ttu-id="e412b-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e412b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e412b-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e412b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e412b-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e412b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e412b-117">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e412b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
