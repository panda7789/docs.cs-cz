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
ms.openlocfilehash: 5d01ab0b6b5d489b2181056129e22661a50108a3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084847"
---
# <a name="icordebugeval2newparameterizedobject-method"></a><span data-ttu-id="0da3e-102">ICorDebugEval2::NewParameterizedObject – metoda</span><span class="sxs-lookup"><span data-stu-id="0da3e-102">ICorDebugEval2::NewParameterizedObject Method</span></span>
<span data-ttu-id="0da3e-103">Vytvoří instanci nového parametrizovaného typu objektu a zavolá metodu konstruktoru objektu.</span><span class="sxs-lookup"><span data-stu-id="0da3e-103">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0da3e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0da3e-104">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedObject (  
    [in] ICorDebugFunction     *pConstructor,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0da3e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0da3e-105">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="0da3e-106">pro Ukazatel na objekt ICorDebugFunction, který představuje konstruktor objektu, který má být vytvořen.</span><span class="sxs-lookup"><span data-stu-id="0da3e-106">[in] A pointer to an ICorDebugFunction object that represents the constructor of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="0da3e-107">pro Počet předaných argumentů typu.</span><span class="sxs-lookup"><span data-stu-id="0da3e-107">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="0da3e-108">pro Pole ukazatelů, z nichž každý odkazuje na objekt ICorDebugType, který představuje argument typu pro objekt, který je právě vytvořen.</span><span class="sxs-lookup"><span data-stu-id="0da3e-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="0da3e-109">pro Počet argumentů předaných konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="0da3e-109">[in] The number of arguments passed to the constructor.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="0da3e-110">pro Pole ukazatelů, z nichž každý odkazuje na objekt ICorDebugValue, který představuje hodnotu argumentu, která je předána konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="0da3e-110">[in] An array of pointers, each of which points to an ICorDebugValue object that represents an argument value that is passed to the constructor.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0da3e-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0da3e-111">Remarks</span></span>  
 <span data-ttu-id="0da3e-112">Konstruktor objektu může převzít parametry <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="0da3e-112">The object's constructor may take <xref:System.Type> parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0da3e-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0da3e-113">Requirements</span></span>  
 <span data-ttu-id="0da3e-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0da3e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0da3e-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0da3e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0da3e-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0da3e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0da3e-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0da3e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
