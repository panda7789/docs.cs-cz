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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c2d6a66eca080b480b508afea36c33b3e0aeec0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178227"
---
# <a name="icordebugevalnewobject-method"></a><span data-ttu-id="971be-102">ICorDebugEval::NewObject – metoda</span><span class="sxs-lookup"><span data-stu-id="971be-102">ICorDebugEval::NewObject Method</span></span>
<span data-ttu-id="971be-103">Přidělí novou instanci objektu a volá metodu zadaný konstruktor.</span><span class="sxs-lookup"><span data-stu-id="971be-103">Allocates a new object instance and calls the specified constructor method.</span></span>  
  
 <span data-ttu-id="971be-104">Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="971be-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="971be-105">Použití [icordebugeval2::newparameterizedobject –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) místo.</span><span class="sxs-lookup"><span data-stu-id="971be-105">Use [ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="971be-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="971be-106">Syntax</span></span>  
  
```  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="971be-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="971be-107">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="971be-108">[in] Konstruktor, který má být volána.</span><span class="sxs-lookup"><span data-stu-id="971be-108">[in] The constructor to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="971be-109">[in] Velikost `ppArgs` pole.</span><span class="sxs-lookup"><span data-stu-id="971be-109">[in] The size of the `ppArgs` array.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="971be-110">[in] Pole objektů ICorDebugValue, z nichž každý představuje argument předaný do konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="971be-110">[in] An array of ICorDebugValue objects, each of which represents an argument to be passed to the constructor.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="971be-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="971be-111">Requirements</span></span>  
 <span data-ttu-id="971be-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="971be-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="971be-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="971be-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="971be-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="971be-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="971be-115">**Verze rozhraní .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="971be-115">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="971be-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="971be-116">See also</span></span>

- [<span data-ttu-id="971be-117">NewParameterizedObject – metoda</span><span class="sxs-lookup"><span data-stu-id="971be-117">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)
