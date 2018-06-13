---
title: ICorDebugEval2::NewParameterizedObject – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObject
helpviewer_keywords:
- NewParameterizedObject method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObject method [.NET Framework debugging]
ms.assetid: 3d705463-e640-4249-8036-4e8206d03cfe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f20c24984aadd05139d1a427b75bc65438539ff1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412802"
---
# <a name="icordebugeval2newparameterizedobject-method"></a><span data-ttu-id="66c2f-102">ICorDebugEval2::NewParameterizedObject – metoda</span><span class="sxs-lookup"><span data-stu-id="66c2f-102">ICorDebugEval2::NewParameterizedObject Method</span></span>
<span data-ttu-id="66c2f-103">Vytvoří nový objekt parametrizované typu a volá konstruktor metodu objektu.</span><span class="sxs-lookup"><span data-stu-id="66c2f-103">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66c2f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66c2f-104">Syntax</span></span>  
  
```  
HRESULT NewParameterizedObject (  
    [in] ICorDebugFunction     *pConstructor,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="66c2f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="66c2f-105">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="66c2f-106">[v] Ukazatel na ICorDebugFunction objekt, který reprezentuje konstruktoru objekt, který má být vytvořena instance.</span><span class="sxs-lookup"><span data-stu-id="66c2f-106">[in] A pointer to an ICorDebugFunction object that represents the constructor of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="66c2f-107">[v] Počet argumentů předaných.</span><span class="sxs-lookup"><span data-stu-id="66c2f-107">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="66c2f-108">[v] Pole ukazatele, každý z nich odkazuje na objekt ICorDebugType, který reprezentuje typ argumentu pro objekt, který je vytvořena instance.</span><span class="sxs-lookup"><span data-stu-id="66c2f-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="66c2f-109">[v] Počet argumentů předaných konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="66c2f-109">[in] The number of arguments passed to the constructor.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="66c2f-110">[v] Pole ukazatele, každý z nich odkazuje na objekt ICorDebugValue, který představuje hodnota argumentu předaného konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="66c2f-110">[in] An array of pointers, each of which points to an ICorDebugValue object that represents an argument value that is passed to the constructor.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66c2f-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="66c2f-111">Remarks</span></span>  
 <span data-ttu-id="66c2f-112">Může trvat objektu konstruktor <xref:System.Type> parametry.</span><span class="sxs-lookup"><span data-stu-id="66c2f-112">The object's constructor may take <xref:System.Type> parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66c2f-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66c2f-113">Requirements</span></span>  
 <span data-ttu-id="66c2f-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66c2f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66c2f-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="66c2f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66c2f-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66c2f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66c2f-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66c2f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
