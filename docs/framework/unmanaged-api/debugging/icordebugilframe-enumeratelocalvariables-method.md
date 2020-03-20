---
title: ICorDebugILFrame::EnumerateLocalVariables – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateLocalVariables
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateLocalVariables
helpviewer_keywords:
- EnumerateLocalVariables method [.NET Framework debugging]
- ICorDebugILFrame::EnumerateLocalVariables method [.NET Framework debugging]
ms.assetid: 1a67fa1b-2419-4cd0-aad4-6f46a0719b4b
topic_type:
- apiref
ms.openlocfilehash: c071a7ddb7d8d3f0e6487ab85284c45f9a7f0372
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178843"
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a><span data-ttu-id="336af-102">ICorDebugILFrame::EnumerateLocalVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="336af-102">ICorDebugILFrame::EnumerateLocalVariables Method</span></span>
<span data-ttu-id="336af-103">Získá čítač pro místní proměnné v tomto rámci.</span><span class="sxs-lookup"><span data-stu-id="336af-103">Gets an enumerator for the local variables in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="336af-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="336af-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateLocalVariables(
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="336af-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="336af-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="336af-106">[out] Ukazatel na adresu objektu ICorDebugValueEnum, který je čítatelem pro místní proměnné v tomto rámci.</span><span class="sxs-lookup"><span data-stu-id="336af-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="336af-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="336af-107">Remarks</span></span>  
 <span data-ttu-id="336af-108">`EnumerateLocalVariables`získá čítač výčtu, který může seznam místních proměnných, které jsou k dispozici v rámci volání, který je reprezentován tento objekt ICorDebugILFrame.</span><span class="sxs-lookup"><span data-stu-id="336af-108">`EnumerateLocalVariables` gets an enumerator that can list the local variables available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="336af-109">Seznam nemusí obsahovat všechny místní proměnné v spuštěné funkci, protože některé z nich nemusí být aktivní.</span><span class="sxs-lookup"><span data-stu-id="336af-109">The list may not include all of the local variables in the running function, because some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="336af-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="336af-110">Requirements</span></span>  
 <span data-ttu-id="336af-111">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="336af-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="336af-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="336af-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="336af-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="336af-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="336af-114">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="336af-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
