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
ms.openlocfilehash: aae5f4c79acd6f92d42c2890ba64fa66e1b4bfbe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753586"
---
# <a name="icordebugeval2newparameterizedobject-method"></a><span data-ttu-id="77274-102">ICorDebugEval2::NewParameterizedObject – metoda</span><span class="sxs-lookup"><span data-stu-id="77274-102">ICorDebugEval2::NewParameterizedObject Method</span></span>
<span data-ttu-id="77274-103">Vytvoří nový objekt typ s parametry a volání metody konstruktoru objektu.</span><span class="sxs-lookup"><span data-stu-id="77274-103">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77274-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77274-104">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedObject (  
    [in] ICorDebugFunction     *pConstructor,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77274-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="77274-105">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="77274-106">[in] Ukazatel na objekt ICorDebugFunction představující konstruktor objektu má být vytvořena.</span><span class="sxs-lookup"><span data-stu-id="77274-106">[in] A pointer to an ICorDebugFunction object that represents the constructor of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="77274-107">[in] Byl předán počet argumentů typu.</span><span class="sxs-lookup"><span data-stu-id="77274-107">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="77274-108">[in] Pole ukazatelů, každý z nich odkazuje na objekt ICorDebugType, který představuje argument typu pro objekt, který je vytvořena instance.</span><span class="sxs-lookup"><span data-stu-id="77274-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="77274-109">[in] Počet argumentů předaný konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="77274-109">[in] The number of arguments passed to the constructor.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="77274-110">[in] Pole ukazatelů, každý z nich odkazuje na objekt ICorDebugValue, který reprezentuje hodnota argumentu, který je předán konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="77274-110">[in] An array of pointers, each of which points to an ICorDebugValue object that represents an argument value that is passed to the constructor.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77274-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="77274-111">Remarks</span></span>  
 <span data-ttu-id="77274-112">Konstruktor objektu může trvat <xref:System.Type> parametry.</span><span class="sxs-lookup"><span data-stu-id="77274-112">The object's constructor may take <xref:System.Type> parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77274-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="77274-113">Requirements</span></span>  
 <span data-ttu-id="77274-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77274-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77274-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="77274-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77274-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77274-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77274-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77274-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
