---
title: "ICorDebugEval2::NewParameterizedObjectNoConstructor – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2.NewParameterizedObjectNoConstructor
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2::NewParameterizedObjectNoConstructor
helpviewer_keywords:
- NewParameterizedObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObjectNoConstructor method [.NET Framework debugging]
ms.assetid: f15b5b78-94f4-4eb9-b3b3-a621272f357c
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 94cf9e0596e8e5cbd59da319247ced6780d0accb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a><span data-ttu-id="f17a5-102">ICorDebugEval2::NewParameterizedObjectNoConstructor – metoda</span><span class="sxs-lookup"><span data-stu-id="f17a5-102">ICorDebugEval2::NewParameterizedObjectNoConstructor Method</span></span>
<span data-ttu-id="f17a5-103">Vytvoří nový objekt parametrizované typ zadané třídy bez pokus o volání metody konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="f17a5-103">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f17a5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f17a5-104">Syntax</span></span>  
  
```  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f17a5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f17a5-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="f17a5-106">[v] Ukazatel na ICorDebugClass objekt, který představuje třídu objekt, který má být vytvořena instance.</span><span class="sxs-lookup"><span data-stu-id="f17a5-106">[in] A pointer to an ICorDebugClass object that represents the class of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="f17a5-107">[v] Počet argumentů předaných.</span><span class="sxs-lookup"><span data-stu-id="f17a5-107">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="f17a5-108">[v] Pole ukazatele, každý z nich odkazuje na objekt ICorDebugType, který reprezentuje typ argumentu pro objekt, který je vytvořena instance.</span><span class="sxs-lookup"><span data-stu-id="f17a5-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f17a5-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f17a5-109">Remarks</span></span>  
 <span data-ttu-id="f17a5-110">`NewParameterizedObjectNoConstructor` Metoda se nezdaří, pokud nesprávný počet argumentů nebo jsou předány nesprávné typy argumenty typu.</span><span class="sxs-lookup"><span data-stu-id="f17a5-110">The `NewParameterizedObjectNoConstructor` method will fail if an incorrect number of type arguments or the wrong types of type arguments are passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f17a5-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f17a5-111">Requirements</span></span>  
 <span data-ttu-id="f17a5-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f17a5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f17a5-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f17a5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f17a5-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f17a5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f17a5-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f17a5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
