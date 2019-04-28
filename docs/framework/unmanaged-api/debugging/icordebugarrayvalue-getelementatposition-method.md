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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 76100116f2ca3a9b9a99477ca2352d5fa1335ab2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645679"
---
# <a name="icordebugarrayvaluegetelementatposition-method"></a><span data-ttu-id="f40e3-102">ICorDebugArrayValue::GetElementAtPosition – metoda</span><span class="sxs-lookup"><span data-stu-id="f40e3-102">ICorDebugArrayValue::GetElementAtPosition Method</span></span>
<span data-ttu-id="f40e3-103">Získá prvek na dané pozici, zpracuje pole jako pole s nulovým základem, jednorozměrné.</span><span class="sxs-lookup"><span data-stu-id="f40e3-103">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f40e3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f40e3-104">Syntax</span></span>  
  
```  
HRESULT GetElementAtPosition (  
    [in]  ULONG32          nPosition,  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f40e3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f40e3-105">Parameters</span></span>  
 `nPosition`  
 <span data-ttu-id="f40e3-106">[in] Pozice prvku, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="f40e3-106">[in] The position of the element to be retrieved.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="f40e3-107">[out] Ukazatel na adresu ICorDebugValue objekt, který představuje hodnotu elementu.</span><span class="sxs-lookup"><span data-stu-id="f40e3-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the element.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f40e3-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f40e3-108">Remarks</span></span>  
 <span data-ttu-id="f40e3-109">Rozložení multidimenzionální pole se řídí styl C++ pole rozložení.</span><span class="sxs-lookup"><span data-stu-id="f40e3-109">The layout of a multi-dimension array follows the C++ style of array layout.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f40e3-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f40e3-110">Requirements</span></span>  
 <span data-ttu-id="f40e3-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f40e3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f40e3-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f40e3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f40e3-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f40e3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f40e3-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f40e3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
