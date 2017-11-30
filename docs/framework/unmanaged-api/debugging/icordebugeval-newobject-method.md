---
title: "ICorDebugEval::NewObject – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.NewObject
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::NewObject
helpviewer_keywords:
- NewObject method [.NET Framework debugging]
- ICorDebugEval::NewObject method [.NET Framework debugging]
ms.assetid: ce3025e8-defa-4c5e-8298-f49d71fa5736
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3e478f057b3c319d099b0156188f3d1e23bb82e8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugevalnewobject-method"></a><span data-ttu-id="ca412-102">ICorDebugEval::NewObject – metoda</span><span class="sxs-lookup"><span data-stu-id="ca412-102">ICorDebugEval::NewObject Method</span></span>
<span data-ttu-id="ca412-103">Přidělí nové instance objektu a volá metodu zadané konstruktor.</span><span class="sxs-lookup"><span data-stu-id="ca412-103">Allocates a new object instance and calls the specified constructor method.</span></span>  
  
 <span data-ttu-id="ca412-104">Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="ca412-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="ca412-105">Použití [icordebugeval2::newparameterizedobject –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) místo.</span><span class="sxs-lookup"><span data-stu-id="ca412-105">Use [ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca412-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca412-106">Syntax</span></span>  
  
```  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ca412-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="ca412-107">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="ca412-108">[v] Konstruktor, který má být volána.</span><span class="sxs-lookup"><span data-stu-id="ca412-108">[in] The constructor to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="ca412-109">[v] Velikost `ppArgs` pole.</span><span class="sxs-lookup"><span data-stu-id="ca412-109">[in] The size of the `ppArgs` array.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="ca412-110">[v] Pole objektů ICorDebugValue, z nichž každý představuje argument mají být předány konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="ca412-110">[in] An array of ICorDebugValue objects, each of which represents an argument to be passed to the constructor.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca412-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ca412-111">Requirements</span></span>  
 <span data-ttu-id="ca412-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca412-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca412-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca412-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca412-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca412-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca412-115">**Verze rozhraní .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="ca412-115">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca412-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="ca412-116">See Also</span></span>  
 [<span data-ttu-id="ca412-117">Newparameterizedobject – metoda</span><span class="sxs-lookup"><span data-stu-id="ca412-117">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)
