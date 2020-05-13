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
ms.openlocfilehash: 7a089831c39c36b0f8a0c7746e95a96e4ddfc5d9
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209393"
---
# <a name="icordebugfunctiongetclass-method"></a><span data-ttu-id="2aa23-102">ICorDebugFunction::GetClass – metoda</span><span class="sxs-lookup"><span data-stu-id="2aa23-102">ICorDebugFunction::GetClass Method</span></span>
<span data-ttu-id="2aa23-103">Získá objekt ICorDebugClass, který představuje třídu, na kterou je tato funkce členem.</span><span class="sxs-lookup"><span data-stu-id="2aa23-103">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2aa23-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2aa23-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2aa23-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2aa23-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="2aa23-106">mimo Ukazatel na adresu `ICorDebugClass` objektu, který představuje třídu, nebo hodnotu null, pokud tato funkce není členem třídy.</span><span class="sxs-lookup"><span data-stu-id="2aa23-106">[out] A pointer to the address of the `ICorDebugClass` object that represents the class, or null, if this function is not a member of a class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2aa23-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2aa23-107">Requirements</span></span>  
 <span data-ttu-id="2aa23-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2aa23-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2aa23-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2aa23-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2aa23-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2aa23-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2aa23-111">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2aa23-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
