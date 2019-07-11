---
title: ICorDebugFrame::GetStackRange – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetStackRange
helpviewer_keywords:
- GetStackRange method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetStackRange method [.NET Framework debugging]
ms.assetid: fab037cb-fda6-40fb-9367-921e435dd5a0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c9f58e66286f5e3e169507efd2f87ce10e9d323b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754854"
---
# <a name="icordebugframegetstackrange-method"></a><span data-ttu-id="3149a-102">ICorDebugFrame::GetStackRange – metoda</span><span class="sxs-lookup"><span data-stu-id="3149a-102">ICorDebugFrame::GetStackRange Method</span></span>
<span data-ttu-id="3149a-103">Získá absolutní adresu rozsahu tohoto rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="3149a-103">Gets the absolute address range of this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3149a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3149a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3149a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3149a-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="3149a-106">[out] Ukazatel `CORDB_ADDRESS` určující počáteční adresu zásobníku představovaného tímto rozhraním `ICorDebugFrame` objektu.</span><span class="sxs-lookup"><span data-stu-id="3149a-106">[out] A pointer to a `CORDB_ADDRESS` that specifies the starting address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="3149a-107">[out] Ukazatel `CORDB_ADDRESS` , který určuje koncovou adresu zásobníku představovaného tímto rozhraním `ICorDebugFrame` objektu.</span><span class="sxs-lookup"><span data-stu-id="3149a-107">[out] A pointer to a `CORDB_ADDRESS` that specifies the ending address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3149a-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3149a-108">Remarks</span></span>  
 <span data-ttu-id="3149a-109">Rozsah adres zásobníku je užitečné pro piecing společně trasování zásobníků shromážděných z více ladicí moduly.</span><span class="sxs-lookup"><span data-stu-id="3149a-109">The address range of the stack is useful for piecing together interleaved stack traces gathered from multiple debugging engines.</span></span> <span data-ttu-id="3149a-110">Číselný rozsah poskytuje žádné informace o obsahu tohoto rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="3149a-110">The numeric range provides no information about the contents of the stack frame.</span></span> <span data-ttu-id="3149a-111">To má smysl pouze pro porovnání umístění rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="3149a-111">It is meaningful only for comparison of stack frame locations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3149a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3149a-112">Requirements</span></span>  
 <span data-ttu-id="3149a-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3149a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3149a-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3149a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3149a-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3149a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3149a-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3149a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
