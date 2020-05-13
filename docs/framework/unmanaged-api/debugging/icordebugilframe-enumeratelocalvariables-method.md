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
ms.openlocfilehash: ad1a91e42f582ce96906da5cbf00ca89acb18499
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210290"
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a><span data-ttu-id="ac22c-102">ICorDebugILFrame::EnumerateLocalVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="ac22c-102">ICorDebugILFrame::EnumerateLocalVariables Method</span></span>
<span data-ttu-id="ac22c-103">Získá enumerátor pro místní proměnné v tomto snímku.</span><span class="sxs-lookup"><span data-stu-id="ac22c-103">Gets an enumerator for the local variables in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac22c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac22c-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateLocalVariables(
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac22c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ac22c-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="ac22c-106">mimo Ukazatel na adresu objektu ICorDebugValueEnum, který je enumerátorem místních proměnných v tomto snímku.</span><span class="sxs-lookup"><span data-stu-id="ac22c-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac22c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ac22c-107">Remarks</span></span>  
 <span data-ttu-id="ac22c-108">`EnumerateLocalVariables`Získá enumerátor, který může zobrazit seznam místních proměnných dostupných v rámci volání, který je reprezentován tímto objektem ICorDebugILFrame.</span><span class="sxs-lookup"><span data-stu-id="ac22c-108">`EnumerateLocalVariables` gets an enumerator that can list the local variables available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="ac22c-109">Seznam nesmí obsahovat všechny místní proměnné ve spuštěné funkci, protože některé z nich nemusí být aktivní.</span><span class="sxs-lookup"><span data-stu-id="ac22c-109">The list may not include all of the local variables in the running function, because some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac22c-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ac22c-110">Requirements</span></span>  
 <span data-ttu-id="ac22c-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac22c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac22c-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ac22c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac22c-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ac22c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac22c-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac22c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
