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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4434f5d0eaa45c9cfcbadb20b29564f0643a2dc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754445"
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a><span data-ttu-id="0ce92-102">ICorDebugEval2::NewParameterizedObjectNoConstructor – metoda</span><span class="sxs-lookup"><span data-stu-id="0ce92-102">ICorDebugEval2::NewParameterizedObjectNoConstructor Method</span></span>
<span data-ttu-id="0ce92-103">Vytvoří nový objekt typ s parametry ze zadané třídy bez pokusu o volání metody konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="0ce92-103">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ce92-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ce92-104">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ce92-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0ce92-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="0ce92-106">[in] Ukazatel na objekt ICorDebugClass, který představuje třídu objektu, který má být vytvořena.</span><span class="sxs-lookup"><span data-stu-id="0ce92-106">[in] A pointer to an ICorDebugClass object that represents the class of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="0ce92-107">[in] Byl předán počet argumentů typu.</span><span class="sxs-lookup"><span data-stu-id="0ce92-107">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="0ce92-108">[in] Pole ukazatelů, každý z nich odkazuje na objekt ICorDebugType, který představuje argument typu pro objekt, který je vytvořena instance.</span><span class="sxs-lookup"><span data-stu-id="0ce92-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ce92-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0ce92-109">Remarks</span></span>  
 <span data-ttu-id="0ce92-110">`NewParameterizedObjectNoConstructor` Metoda selže, pokud nesprávný počet argumentů typu nebo jsou předány nesprávné typy argumentů typu.</span><span class="sxs-lookup"><span data-stu-id="0ce92-110">The `NewParameterizedObjectNoConstructor` method will fail if an incorrect number of type arguments or the wrong types of type arguments are passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ce92-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0ce92-111">Requirements</span></span>  
 <span data-ttu-id="0ce92-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ce92-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ce92-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0ce92-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ce92-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ce92-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ce92-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ce92-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
