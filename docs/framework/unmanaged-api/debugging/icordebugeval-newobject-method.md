---
title: ICorDebugEval::NewObject – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObject
helpviewer_keywords:
- NewObject method [.NET Framework debugging]
- ICorDebugEval::NewObject method [.NET Framework debugging]
ms.assetid: ce3025e8-defa-4c5e-8298-f49d71fa5736
topic_type:
- apiref
ms.openlocfilehash: 68a7e911c2bd1798ea8f34f6a6e24299fe68775d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137624"
---
# <a name="icordebugevalnewobject-method"></a><span data-ttu-id="d8fae-102">ICorDebugEval::NewObject – metoda</span><span class="sxs-lookup"><span data-stu-id="d8fae-102">ICorDebugEval::NewObject Method</span></span>
<span data-ttu-id="d8fae-103">Přidělí novou instanci objektu a zavolá specifikovanou metodu konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="d8fae-103">Allocates a new object instance and calls the specified constructor method.</span></span>  
  
 <span data-ttu-id="d8fae-104">Tato metoda je zastaralá ve verzi .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="d8fae-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="d8fae-105">Místo toho použijte [ICorDebugEval2:: newparameterizedobject –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d8fae-105">Use [ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8fae-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8fae-106">Syntax</span></span>  
  
```cpp  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8fae-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8fae-107">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="d8fae-108">pro Konstruktor, který má být volán.</span><span class="sxs-lookup"><span data-stu-id="d8fae-108">[in] The constructor to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="d8fae-109">pro Velikost pole `ppArgs`.</span><span class="sxs-lookup"><span data-stu-id="d8fae-109">[in] The size of the `ppArgs` array.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="d8fae-110">pro Pole objektů ICorDebugValue, z nichž každý představuje argument, který má být předán konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="d8fae-110">[in] An array of ICorDebugValue objects, each of which represents an argument to be passed to the constructor.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8fae-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d8fae-111">Requirements</span></span>  
 <span data-ttu-id="d8fae-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8fae-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8fae-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d8fae-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8fae-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d8fae-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8fae-115">**Verze .NET Framework:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="d8fae-115">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8fae-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d8fae-116">See also</span></span>

- [<span data-ttu-id="d8fae-117">NewParameterizedObject – metoda</span><span class="sxs-lookup"><span data-stu-id="d8fae-117">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)
