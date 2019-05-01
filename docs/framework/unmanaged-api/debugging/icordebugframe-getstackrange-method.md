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
ms.openlocfilehash: 43532888d181adcb7a7e3760f2a5e3d8f664a35c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995810"
---
# <a name="icordebugframegetstackrange-method"></a><span data-ttu-id="37c06-102">ICorDebugFrame::GetStackRange – metoda</span><span class="sxs-lookup"><span data-stu-id="37c06-102">ICorDebugFrame::GetStackRange Method</span></span>
<span data-ttu-id="37c06-103">Získá absolutní adresu rozsahu tohoto rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="37c06-103">Gets the absolute address range of this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37c06-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37c06-104">Syntax</span></span>  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37c06-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="37c06-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="37c06-106">[out] Ukazatel `CORDB_ADDRESS` určující počáteční adresu zásobníku představovaného tímto rozhraním `ICorDebugFrame` objektu.</span><span class="sxs-lookup"><span data-stu-id="37c06-106">[out] A pointer to a `CORDB_ADDRESS` that specifies the starting address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="37c06-107">[out] Ukazatel `CORDB_ADDRESS` , který určuje koncovou adresu zásobníku představovaného tímto rozhraním `ICorDebugFrame` objektu.</span><span class="sxs-lookup"><span data-stu-id="37c06-107">[out] A pointer to a `CORDB_ADDRESS` that specifies the ending address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37c06-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="37c06-108">Remarks</span></span>  
 <span data-ttu-id="37c06-109">Rozsah adres zásobníku je užitečné pro piecing společně trasování zásobníků shromážděných z více ladicí moduly.</span><span class="sxs-lookup"><span data-stu-id="37c06-109">The address range of the stack is useful for piecing together interleaved stack traces gathered from multiple debugging engines.</span></span> <span data-ttu-id="37c06-110">Číselný rozsah poskytuje žádné informace o obsahu tohoto rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="37c06-110">The numeric range provides no information about the contents of the stack frame.</span></span> <span data-ttu-id="37c06-111">To má smysl pouze pro porovnání umístění rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="37c06-111">It is meaningful only for comparison of stack frame locations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37c06-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="37c06-112">Requirements</span></span>  
 <span data-ttu-id="37c06-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37c06-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37c06-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="37c06-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="37c06-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37c06-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37c06-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37c06-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
