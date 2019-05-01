---
title: ICorDebugFunction::GetClass – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetClass
helpviewer_keywords:
- GetClass method, ICorDebugFunction interface [.NET Framework debugging]
- ICorDebugFunction::GetClass method [.NET Framework debugging]
ms.assetid: 27967230-144f-40d3-9e23-961d0241abd9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea71e984be42e3b1a7b4b9fa6df878aca911c412
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995758"
---
# <a name="icordebugfunctiongetclass-method"></a><span data-ttu-id="58906-102">ICorDebugFunction::GetClass – metoda</span><span class="sxs-lookup"><span data-stu-id="58906-102">ICorDebugFunction::GetClass Method</span></span>
<span data-ttu-id="58906-103">Získá ICorDebugClass objekt, který představuje třídu, tato funkce je členem skupiny.</span><span class="sxs-lookup"><span data-stu-id="58906-103">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58906-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58906-104">Syntax</span></span>  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58906-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="58906-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="58906-106">[out] Ukazatel na adresu `ICorDebugClass` objekt, který představuje třídu nebo hodnota null, pokud tato funkce není členem třídy.</span><span class="sxs-lookup"><span data-stu-id="58906-106">[out] A pointer to the address of the `ICorDebugClass` object that represents the class, or null, if this function is not a member of a class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58906-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="58906-107">Requirements</span></span>  
 <span data-ttu-id="58906-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58906-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58906-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58906-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58906-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58906-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58906-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58906-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
