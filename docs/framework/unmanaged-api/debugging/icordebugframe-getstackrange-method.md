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
ms.openlocfilehash: cacdccf5c27cd1d115134d49e754b4ace2870b72
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205159"
---
# <a name="icordebugframegetstackrange-method"></a><span data-ttu-id="8b414-102">ICorDebugFrame::GetStackRange – metoda</span><span class="sxs-lookup"><span data-stu-id="8b414-102">ICorDebugFrame::GetStackRange Method</span></span>
<span data-ttu-id="8b414-103">Získá absolutní rozsah adres tohoto rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="8b414-103">Gets the absolute address range of this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b414-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b414-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b414-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b414-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="8b414-106">mimo Ukazatel na `CORDB_ADDRESS` , který určuje počáteční adresu rámce zásobníku reprezentované tímto `ICorDebugFrame` objektem.</span><span class="sxs-lookup"><span data-stu-id="8b414-106">[out] A pointer to a `CORDB_ADDRESS` that specifies the starting address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="8b414-107">mimo Ukazatel na `CORDB_ADDRESS` , který určuje koncovou adresu rámce zásobníku reprezentované tímto `ICorDebugFrame` objektem.</span><span class="sxs-lookup"><span data-stu-id="8b414-107">[out] A pointer to a `CORDB_ADDRESS` that specifies the ending address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b414-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8b414-108">Remarks</span></span>  
 <span data-ttu-id="8b414-109">Rozsah adres zásobníku je užitečný pro piecing společně prokládaných trasování zásobníku shromážděných z několika ladicích modulů.</span><span class="sxs-lookup"><span data-stu-id="8b414-109">The address range of the stack is useful for piecing together interleaved stack traces gathered from multiple debugging engines.</span></span> <span data-ttu-id="8b414-110">Číselný rozsah neposkytuje žádné informace o obsahu rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="8b414-110">The numeric range provides no information about the contents of the stack frame.</span></span> <span data-ttu-id="8b414-111">Má smysl jenom pro porovnání umístění rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="8b414-111">It is meaningful only for comparison of stack frame locations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b414-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8b414-112">Requirements</span></span>  
 <span data-ttu-id="8b414-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b414-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b414-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8b414-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b414-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8b414-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b414-116">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b414-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
