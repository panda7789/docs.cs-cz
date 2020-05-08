---
title: ICorDebugEval2::NewParameterizedObjectNoConstructor – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObjectNoConstructor
helpviewer_keywords:
- NewParameterizedObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObjectNoConstructor method [.NET Framework debugging]
ms.assetid: f15b5b78-94f4-4eb9-b3b3-a621272f357c
topic_type:
- apiref
ms.openlocfilehash: 90fce1710f97341fb49be1d07f7af2edf8cb848c
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976080"
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a><span data-ttu-id="34013-102">ICorDebugEval2::NewParameterizedObjectNoConstructor – metoda</span><span class="sxs-lookup"><span data-stu-id="34013-102">ICorDebugEval2::NewParameterizedObjectNoConstructor Method</span></span>
<span data-ttu-id="34013-103">Vytvoří instanci nového parametrizovaného typu objektu zadané třídy bez pokusu o volání metody konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="34013-103">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34013-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34013-104">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34013-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="34013-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="34013-106">pro Ukazatel na objekt ICorDebugClass, který představuje třídu objektu, který má být vytvořen.</span><span class="sxs-lookup"><span data-stu-id="34013-106">[in] A pointer to an ICorDebugClass object that represents the class of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="34013-107">pro Počet předaných argumentů typu.</span><span class="sxs-lookup"><span data-stu-id="34013-107">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="34013-108">pro Pole ukazatelů, z nichž každý odkazuje na objekt ICorDebugType, který představuje argument typu pro objekt, který je právě vytvořen.</span><span class="sxs-lookup"><span data-stu-id="34013-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34013-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="34013-109">Remarks</span></span>  
 <span data-ttu-id="34013-110">`NewParameterizedObjectNoConstructor` Metoda selže, pokud je předán nesprávný počet argumentů typu nebo nesprávné typy argumentů typu.</span><span class="sxs-lookup"><span data-stu-id="34013-110">The `NewParameterizedObjectNoConstructor` method will fail if an incorrect number of type arguments or the wrong types of type arguments are passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34013-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="34013-111">Requirements</span></span>  
 <span data-ttu-id="34013-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34013-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34013-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="34013-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="34013-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="34013-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34013-115">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34013-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
