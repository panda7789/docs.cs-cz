---
title: ICorDebugEval::NewObjectNoConstructor – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObjectNoConstructor
helpviewer_keywords:
- NewObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval::NewObjectNoConstructor method [.NET Framework debugging]
ms.assetid: 80d509ca-b5e3-4c46-9c14-800db73d9bf7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d9db6853d3bd4bb7faae54b746a5a940c7dec8a8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561788"
---
# <a name="icordebugevalnewobjectnoconstructor-method"></a><span data-ttu-id="f2924-102">ICorDebugEval::NewObjectNoConstructor – metoda</span><span class="sxs-lookup"><span data-stu-id="f2924-102">ICorDebugEval::NewObjectNoConstructor Method</span></span>
<span data-ttu-id="f2924-103">Přidělí novou instanci objektu zadaného typu, bez pokusu o volání metody konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="f2924-103">Allocates a new object instance of the specified type, without attempting to call a constructor method.</span></span>  
  
 <span data-ttu-id="f2924-104">Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="f2924-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="f2924-105">Použití [icordebugeval2::newparameterizedobjectnoconstructor –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) místo.</span><span class="sxs-lookup"><span data-stu-id="f2924-105">Use [ICorDebugEval2::NewParameterizedObjectNoConstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2924-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2924-106">Syntax</span></span>  
  
```  
HRESULT NewObjectNoConstructor (  
    [in] ICorDebugClass     *pClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f2924-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="f2924-107">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="f2924-108">[in] Ukazatel na objekt ICorDebugClass, který představuje typ objektu, který má být vytvořena.</span><span class="sxs-lookup"><span data-stu-id="f2924-108">[in] Pointer to an ICorDebugClass object that represents the type of object to be instantiated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2924-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f2924-109">Requirements</span></span>  
 <span data-ttu-id="f2924-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2924-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2924-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f2924-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2924-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2924-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2924-113">**Verze rozhraní .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="f2924-113">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2924-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2924-114">See also</span></span>
- [<span data-ttu-id="f2924-115">NewParameterizedObjectNoConstructor – metoda</span><span class="sxs-lookup"><span data-stu-id="f2924-115">NewParameterizedObjectNoConstructor Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)
