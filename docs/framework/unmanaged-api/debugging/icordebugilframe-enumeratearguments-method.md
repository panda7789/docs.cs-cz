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
ms.openlocfilehash: 499f58cc0a3f2d1b3c159435ed7d9b523f25e29e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757888"
---
# <a name="icordebugilframeenumeratearguments-method"></a><span data-ttu-id="70edc-102">ICorDebugILFrame::EnumerateArguments – metoda</span><span class="sxs-lookup"><span data-stu-id="70edc-102">ICorDebugILFrame::EnumerateArguments Method</span></span>
<span data-ttu-id="70edc-103">Získá enumerátor pro argumenty v tomto snímku.</span><span class="sxs-lookup"><span data-stu-id="70edc-103">Gets an enumerator for the arguments in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70edc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70edc-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70edc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="70edc-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="70edc-106">[out] Ukazatel na adresu icordebugvalueenum – objekt, který je enumerátor pro argumenty v tomto snímku.</span><span class="sxs-lookup"><span data-stu-id="70edc-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the arguments in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70edc-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="70edc-107">Remarks</span></span>  
 <span data-ttu-id="70edc-108">`EnumerateArguments` Získá enumerátor, který můžete zobrazit seznam dostupných v rámci volání, která je reprezentována tímto objektem ICorDebugILFrame argumenty.</span><span class="sxs-lookup"><span data-stu-id="70edc-108">`EnumerateArguments` gets an enumerator that can list the arguments available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="70edc-109">Obsahuje seznam argumentů, které jsou [vararg](/cpp/windows/vararg) (to znamená, proměnný počet argumentů) stejně jako argumenty, které nejsou `vararg`.</span><span class="sxs-lookup"><span data-stu-id="70edc-109">The list will include arguments that are [vararg](/cpp/windows/vararg) (that is, a variable number of arguments) as well as arguments that are not `vararg`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70edc-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="70edc-110">Requirements</span></span>  
 <span data-ttu-id="70edc-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70edc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70edc-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="70edc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70edc-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70edc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70edc-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70edc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
