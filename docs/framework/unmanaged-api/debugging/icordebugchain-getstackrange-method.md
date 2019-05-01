---
title: ICorDebugChain::GetStackRange – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetStackRange
helpviewer_keywords:
- ICorDebugChain::GetStackRange method [.NET Framework debugging]
- GetStackRange method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 554284e7-3f6c-4d40-8da5-1c9317fbd484
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac40927ac9469e4a2fb74fb550287130b9bb9f83
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989453"
---
# <a name="icordebugchaingetstackrange-method"></a><span data-ttu-id="66613-102">ICorDebugChain::GetStackRange – metoda</span><span class="sxs-lookup"><span data-stu-id="66613-102">ICorDebugChain::GetStackRange Method</span></span>
<span data-ttu-id="66613-103">Získá rozsah adres segmentu zásobníku pro tento řetězec.</span><span class="sxs-lookup"><span data-stu-id="66613-103">Gets the address range of the stack segment for this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66613-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66613-104">Syntax</span></span>  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66613-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="66613-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="66613-106">[out] Ukazatel `CORDB_ADDRESS` hodnotu, která je počáteční adresu zásobníku segmentu.</span><span class="sxs-lookup"><span data-stu-id="66613-106">[out] A pointer to a `CORDB_ADDRESS` value that is the starting address of the stack segment.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="66613-107">[out] Ukazatel `CORDB_ADDRESS` hodnotu, která je koncová adresa segment zásobníku.</span><span class="sxs-lookup"><span data-stu-id="66613-107">[out] A pointer to a `CORDB_ADDRESS` value that is the ending address of the stack segment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66613-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="66613-108">Remarks</span></span>  
 <span data-ttu-id="66613-109">Číselný rozsah má smysl pouze pro porovnání umístění rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="66613-109">The numeric range is meaningful only for comparison of stack frame locations.</span></span> <span data-ttu-id="66613-110">Nemůžete nevyvozujte předpoklady o tom, co je ve skutečnosti uložené v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="66613-110">You cannot make any assumptions about what is actually stored on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66613-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66613-111">Requirements</span></span>  
 <span data-ttu-id="66613-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66613-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66613-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="66613-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66613-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66613-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66613-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66613-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
