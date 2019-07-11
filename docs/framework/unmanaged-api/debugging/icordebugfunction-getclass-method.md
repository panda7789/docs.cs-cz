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
ms.openlocfilehash: 218818097846709ec92e20f33a0707314edd562a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754738"
---
# <a name="icordebugfunctiongetclass-method"></a><span data-ttu-id="62f1c-102">ICorDebugFunction::GetClass – metoda</span><span class="sxs-lookup"><span data-stu-id="62f1c-102">ICorDebugFunction::GetClass Method</span></span>
<span data-ttu-id="62f1c-103">Získá ICorDebugClass objekt, který představuje třídu, tato funkce je členem skupiny.</span><span class="sxs-lookup"><span data-stu-id="62f1c-103">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62f1c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62f1c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62f1c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="62f1c-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="62f1c-106">[out] Ukazatel na adresu `ICorDebugClass` objekt, který představuje třídu nebo hodnota null, pokud tato funkce není členem třídy.</span><span class="sxs-lookup"><span data-stu-id="62f1c-106">[out] A pointer to the address of the `ICorDebugClass` object that represents the class, or null, if this function is not a member of a class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62f1c-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="62f1c-107">Requirements</span></span>  
 <span data-ttu-id="62f1c-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62f1c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62f1c-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="62f1c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62f1c-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62f1c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62f1c-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62f1c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
