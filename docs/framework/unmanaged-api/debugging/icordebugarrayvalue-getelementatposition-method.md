---
title: ICorDebugArrayValue::GetElementAtPosition – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElementAtPosition
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElementAtPosition
helpviewer_keywords:
- GetElementAtPosition method [.NET Framework debugging]
- ICorDebugArrayValue::GetElementAtPosition method [.NET Framework debugging]
ms.assetid: 6fd5eaa4-1997-4910-82f5-3887480db764
topic_type:
- apiref
ms.openlocfilehash: 5644c20ec5df2606c7258131573691997f424e50
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895011"
---
# <a name="icordebugarrayvaluegetelementatposition-method"></a><span data-ttu-id="63781-102">ICorDebugArrayValue::GetElementAtPosition – metoda</span><span class="sxs-lookup"><span data-stu-id="63781-102">ICorDebugArrayValue::GetElementAtPosition Method</span></span>
<span data-ttu-id="63781-103">Získá prvek na dané pozici, což zpracuje pole jako jednorozměrné jednorozměrné pole s nulovým základem.</span><span class="sxs-lookup"><span data-stu-id="63781-103">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63781-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63781-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElementAtPosition (  
    [in]  ULONG32          nPosition,  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63781-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="63781-105">Parameters</span></span>  
 `nPosition`  
 <span data-ttu-id="63781-106">pro Pozice prvku, který má být načten.</span><span class="sxs-lookup"><span data-stu-id="63781-106">[in] The position of the element to be retrieved.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="63781-107">mimo Ukazatel na adresu objektu ICorDebugValue, který představuje hodnotu prvku.</span><span class="sxs-lookup"><span data-stu-id="63781-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the element.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63781-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="63781-108">Remarks</span></span>  
 <span data-ttu-id="63781-109">Rozložení pole s více dimenzemi následuje styl C++ rozložení pole.</span><span class="sxs-lookup"><span data-stu-id="63781-109">The layout of a multi-dimension array follows the C++ style of array layout.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63781-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="63781-110">Requirements</span></span>  
 <span data-ttu-id="63781-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63781-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63781-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="63781-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63781-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="63781-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63781-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63781-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
