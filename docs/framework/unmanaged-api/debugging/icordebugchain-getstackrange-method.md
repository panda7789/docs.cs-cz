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
ms.openlocfilehash: 64e697323377d664b7b1e36bbf5931a44465cc51
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178961"
---
# <a name="icordebugchaingetstackrange-method"></a><span data-ttu-id="92c17-102">ICorDebugChain::GetStackRange – metoda</span><span class="sxs-lookup"><span data-stu-id="92c17-102">ICorDebugChain::GetStackRange Method</span></span>
<span data-ttu-id="92c17-103">Získá rozsah adres segmentu zásobníku pro tento řetězec.</span><span class="sxs-lookup"><span data-stu-id="92c17-103">Gets the address range of the stack segment for this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92c17-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92c17-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92c17-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="92c17-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="92c17-106">[out] Ukazatel na `CORDB_ADDRESS` hodnotu, která je počáteční adresou segmentu zásobníku.</span><span class="sxs-lookup"><span data-stu-id="92c17-106">[out] A pointer to a `CORDB_ADDRESS` value that is the starting address of the stack segment.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="92c17-107">[out] Ukazatel na `CORDB_ADDRESS` hodnotu, která je koncovou adresou segmentu zásobníku.</span><span class="sxs-lookup"><span data-stu-id="92c17-107">[out] A pointer to a `CORDB_ADDRESS` value that is the ending address of the stack segment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92c17-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="92c17-108">Remarks</span></span>  
 <span data-ttu-id="92c17-109">Číselný rozsah je smysluplný pouze pro porovnání umístění rámců zásobníku.</span><span class="sxs-lookup"><span data-stu-id="92c17-109">The numeric range is meaningful only for comparison of stack frame locations.</span></span> <span data-ttu-id="92c17-110">Nelze provádět žádné předpoklady o tom, co je skutečně uloženo v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="92c17-110">You cannot make any assumptions about what is actually stored on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92c17-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="92c17-111">Requirements</span></span>  
 <span data-ttu-id="92c17-112">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92c17-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92c17-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92c17-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92c17-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92c17-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92c17-115">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92c17-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
