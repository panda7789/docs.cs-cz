---
title: ICorDebugILFrame::EnumerateArguments – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateArguments
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateArguments
helpviewer_keywords:
- ICorDebugILFrame::EnumerateArguments method [.NET Framework debugging]
- EnumerateArguments method [.NET Framework debugging]
ms.assetid: 00ac81e2-a774-422a-bd88-54a4b3c99f73
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49d7fb1de0b2ea63c1a766023b23acc42e027af8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995563"
---
# <a name="icordebugilframeenumeratearguments-method"></a><span data-ttu-id="3e48a-102">ICorDebugILFrame::EnumerateArguments – metoda</span><span class="sxs-lookup"><span data-stu-id="3e48a-102">ICorDebugILFrame::EnumerateArguments Method</span></span>
<span data-ttu-id="3e48a-103">Získá enumerátor pro argumenty v tomto snímku.</span><span class="sxs-lookup"><span data-stu-id="3e48a-103">Gets an enumerator for the arguments in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e48a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e48a-104">Syntax</span></span>  
  
```  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e48a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3e48a-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="3e48a-106">[out] Ukazatel na adresu icordebugvalueenum – objekt, který je enumerátor pro argumenty v tomto snímku.</span><span class="sxs-lookup"><span data-stu-id="3e48a-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the arguments in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e48a-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3e48a-107">Remarks</span></span>  
 <span data-ttu-id="3e48a-108">`EnumerateArguments` Získá enumerátor, který můžete zobrazit seznam dostupných v rámci volání, která je reprezentována tímto objektem ICorDebugILFrame argumenty.</span><span class="sxs-lookup"><span data-stu-id="3e48a-108">`EnumerateArguments` gets an enumerator that can list the arguments available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="3e48a-109">Obsahuje seznam argumentů, které jsou [vararg](/cpp/windows/vararg) (to znamená, proměnný počet argumentů) stejně jako argumenty, které nejsou `vararg`.</span><span class="sxs-lookup"><span data-stu-id="3e48a-109">The list will include arguments that are [vararg](/cpp/windows/vararg) (that is, a variable number of arguments) as well as arguments that are not `vararg`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e48a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3e48a-110">Requirements</span></span>  
 <span data-ttu-id="3e48a-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e48a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e48a-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3e48a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e48a-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e48a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e48a-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e48a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
