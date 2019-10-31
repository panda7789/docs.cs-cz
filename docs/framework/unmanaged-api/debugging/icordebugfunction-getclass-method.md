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
ms.openlocfilehash: 887d207aea3de9296107c041816606b2f5947406
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124032"
---
# <a name="icordebugfunctiongetclass-method"></a><span data-ttu-id="96a1b-102">ICorDebugFunction::GetClass – metoda</span><span class="sxs-lookup"><span data-stu-id="96a1b-102">ICorDebugFunction::GetClass Method</span></span>
<span data-ttu-id="96a1b-103">Získá objekt ICorDebugClass, který představuje třídu, na kterou je tato funkce členem.</span><span class="sxs-lookup"><span data-stu-id="96a1b-103">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96a1b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96a1b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96a1b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="96a1b-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="96a1b-106">mimo Ukazatel na adresu objektu `ICorDebugClass`, který představuje třídu, nebo hodnotu null, pokud tato funkce není členem třídy.</span><span class="sxs-lookup"><span data-stu-id="96a1b-106">[out] A pointer to the address of the `ICorDebugClass` object that represents the class, or null, if this function is not a member of a class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96a1b-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="96a1b-107">Requirements</span></span>  
 <span data-ttu-id="96a1b-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96a1b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96a1b-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="96a1b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96a1b-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="96a1b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96a1b-111">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96a1b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
