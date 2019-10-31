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
ms.openlocfilehash: 07331a512dd513a94a7d8c3a8d8b0754d998b94b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131005"
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a><span data-ttu-id="a679e-102">ICorDebugILFrame::EnumerateLocalVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="a679e-102">ICorDebugILFrame::EnumerateLocalVariables Method</span></span>
<span data-ttu-id="a679e-103">Získá enumerátor pro místní proměnné v tomto snímku.</span><span class="sxs-lookup"><span data-stu-id="a679e-103">Gets an enumerator for the local variables in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a679e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a679e-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateLocalVariables(   
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a679e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a679e-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="a679e-106">mimo Ukazatel na adresu objektu ICorDebugValueEnum, který je enumerátorem místních proměnných v tomto snímku.</span><span class="sxs-lookup"><span data-stu-id="a679e-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a679e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a679e-107">Remarks</span></span>  
 <span data-ttu-id="a679e-108">`EnumerateLocalVariables` získá enumerátor, který může zobrazit seznam místních proměnných dostupných v rámci volání, který je reprezentován tímto objektem ICorDebugILFrame.</span><span class="sxs-lookup"><span data-stu-id="a679e-108">`EnumerateLocalVariables` gets an enumerator that can list the local variables available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="a679e-109">Seznam nesmí obsahovat všechny místní proměnné ve spuštěné funkci, protože některé z nich nemusí být aktivní.</span><span class="sxs-lookup"><span data-stu-id="a679e-109">The list may not include all of the local variables in the running function, because some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a679e-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a679e-110">Requirements</span></span>  
 <span data-ttu-id="a679e-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a679e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a679e-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a679e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a679e-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a679e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a679e-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a679e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
