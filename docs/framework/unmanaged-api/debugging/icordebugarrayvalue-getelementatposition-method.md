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
ms.openlocfilehash: 10584442d7e0bd61e6decaf2b494dfe39f339d6d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088419"
---
# <a name="icordebugarrayvaluegetelementatposition-method"></a><span data-ttu-id="a6356-102">ICorDebugArrayValue::GetElementAtPosition – metoda</span><span class="sxs-lookup"><span data-stu-id="a6356-102">ICorDebugArrayValue::GetElementAtPosition Method</span></span>
<span data-ttu-id="a6356-103">Získá prvek na dané pozici, což zpracuje pole jako jednorozměrné jednorozměrné pole s nulovým základem.</span><span class="sxs-lookup"><span data-stu-id="a6356-103">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6356-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6356-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElementAtPosition (  
    [in]  ULONG32          nPosition,  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6356-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a6356-105">Parameters</span></span>  
 `nPosition`  
 <span data-ttu-id="a6356-106">pro Pozice prvku, který má být načten.</span><span class="sxs-lookup"><span data-stu-id="a6356-106">[in] The position of the element to be retrieved.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="a6356-107">mimo Ukazatel na adresu objektu ICorDebugValue, který představuje hodnotu prvku.</span><span class="sxs-lookup"><span data-stu-id="a6356-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the element.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6356-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a6356-108">Remarks</span></span>  
 <span data-ttu-id="a6356-109">Rozložení pole s více dimenzemi se řídí C++ stylem rozložení pole.</span><span class="sxs-lookup"><span data-stu-id="a6356-109">The layout of a multi-dimension array follows the C++ style of array layout.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6356-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a6356-110">Requirements</span></span>  
 <span data-ttu-id="a6356-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6356-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6356-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a6356-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a6356-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a6356-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6356-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6356-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
