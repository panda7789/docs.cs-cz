---
title: ICorDebugEval2::CreateValueForType – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CreateValueForType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CreateValueForType
helpviewer_keywords:
- CreateValueForType method [.NET Framework debugging]
- ICorDebugEval2::CreateValueForType method [.NET Framework debugging]
ms.assetid: ea38ae20-7e0a-427a-be77-d78fae719d82
topic_type:
- apiref
ms.openlocfilehash: fd7acaa8bcb4d53893855bcd25ff68cf26e30354
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976158"
---
# <a name="icordebugeval2createvaluefortype-method"></a><span data-ttu-id="313b4-102">ICorDebugEval2::CreateValueForType – metoda</span><span class="sxs-lookup"><span data-stu-id="313b4-102">ICorDebugEval2::CreateValueForType Method</span></span>
<span data-ttu-id="313b4-103">Získá ukazatel na nový ICorDebugValue zadaného typu s počáteční hodnotou 0 nebo null.</span><span class="sxs-lookup"><span data-stu-id="313b4-103">Gets a pointer to a new ICorDebugValue of the specified type, with an initial value of zero or null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="313b4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="313b4-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="313b4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="313b4-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="313b4-106">pro Ukazatel na objekt ICorDebugType, který představuje typ.</span><span class="sxs-lookup"><span data-stu-id="313b4-106">[in] Pointer to an ICorDebugType object that represents the type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="313b4-107">mimo Ukazatel na adresu `ICorDebugValue` objektu, který představuje hodnotu.</span><span class="sxs-lookup"><span data-stu-id="313b4-107">[out] Pointer to the address of an `ICorDebugValue` object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="313b4-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="313b4-108">Remarks</span></span>  
 <span data-ttu-id="313b4-109">`CreateValueForType`generalizes [ICorDebugEval:: CreateValue –](icordebugeval-createvalue-method.md) vám umožní určit libovolný typ objektu, včetně konstruovaných typů, jako je `List<int>`.</span><span class="sxs-lookup"><span data-stu-id="313b4-109">`CreateValueForType` generalizes [ICorDebugEval::CreateValue](icordebugeval-createvalue-method.md) by allowing you to specify an arbitrary object type, including constructed types such as `List<int>`.</span></span> <span data-ttu-id="313b4-110">Jediným účelem této metody je generovat hodnotu, která může být předána vyhodnocení funkce.</span><span class="sxs-lookup"><span data-stu-id="313b4-110">The only purpose of this method is to generate a value that can be passed to a function evaluation.</span></span>  
  
 <span data-ttu-id="313b4-111">Typ musí být typ třída nebo hodnota.</span><span class="sxs-lookup"><span data-stu-id="313b4-111">The type must be a class or a value type.</span></span> <span data-ttu-id="313b4-112">Tuto metodu nelze použít k vytvoření hodnot pole nebo hodnot řetězců.</span><span class="sxs-lookup"><span data-stu-id="313b4-112">You cannot use this method to create array values or string values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="313b4-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="313b4-113">Requirements</span></span>  
 <span data-ttu-id="313b4-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="313b4-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="313b4-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="313b4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="313b4-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="313b4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="313b4-117">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="313b4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
