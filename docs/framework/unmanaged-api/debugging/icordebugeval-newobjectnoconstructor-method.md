---
title: "ICorDebugEval::NewObjectNoConstructor – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.NewObjectNoConstructor
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::NewObjectNoConstructor
helpviewer_keywords:
- NewObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval::NewObjectNoConstructor method [.NET Framework debugging]
ms.assetid: 80d509ca-b5e3-4c46-9c14-800db73d9bf7
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ceb35781d4685e3576470da3b99a6666ba233e19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugevalnewobjectnoconstructor-method"></a><span data-ttu-id="d7fdb-102">ICorDebugEval::NewObjectNoConstructor – metoda</span><span class="sxs-lookup"><span data-stu-id="d7fdb-102">ICorDebugEval::NewObjectNoConstructor Method</span></span>
<span data-ttu-id="d7fdb-103">Bez pokus o volání metody konstruktoru přiděluje novou instanci objektu zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="d7fdb-103">Allocates a new object instance of the specified type, without attempting to call a constructor method.</span></span>  
  
 <span data-ttu-id="d7fdb-104">Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="d7fdb-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="d7fdb-105">Použití [icordebugeval2::newparameterizedobjectnoconstructor –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) místo.</span><span class="sxs-lookup"><span data-stu-id="d7fdb-105">Use [ICorDebugEval2::NewParameterizedObjectNoConstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7fdb-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7fdb-106">Syntax</span></span>  
  
```  
HRESULT NewObjectNoConstructor (  
    [in] ICorDebugClass     *pClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d7fdb-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="d7fdb-107">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="d7fdb-108">[v] Ukazatel na ICorDebugClass objekt, který představuje typ objekt, který má být vytvořena instance.</span><span class="sxs-lookup"><span data-stu-id="d7fdb-108">[in] Pointer to an ICorDebugClass object that represents the type of object to be instantiated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7fdb-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d7fdb-109">Requirements</span></span>  
 <span data-ttu-id="d7fdb-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7fdb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7fdb-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7fdb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7fdb-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7fdb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7fdb-113">**Verze rozhraní .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="d7fdb-113">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7fdb-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7fdb-114">See Also</span></span>  
 [<span data-ttu-id="d7fdb-115">NewParameterizedObjectNoConstructor – metoda</span><span class="sxs-lookup"><span data-stu-id="d7fdb-115">NewParameterizedObjectNoConstructor Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)
