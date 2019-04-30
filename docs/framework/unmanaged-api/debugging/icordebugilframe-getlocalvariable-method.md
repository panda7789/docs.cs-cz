---
title: ICorDebugILFrame::GetLocalVariable – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetLocalVariable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetLocalVariable
helpviewer_keywords:
- ICorDebugILFrame::GetLocalVariable method [.NET Framework debugging]
- GetLocalVariable method [.NET Framework debugging]
ms.assetid: c8706356-d50b-4f87-a40c-39c3b7f4fd38
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ebd36f01297f24c050f84fb67e7673f8641fe206
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789711"
---
# <a name="icordebugilframegetlocalvariable-method"></a><span data-ttu-id="69999-102">ICorDebugILFrame::GetLocalVariable – metoda</span><span class="sxs-lookup"><span data-stu-id="69999-102">ICorDebugILFrame::GetLocalVariable Method</span></span>
<span data-ttu-id="69999-103">Získá hodnotu místní proměnné zadané v tomto bloku zásobníku Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="69999-103">Gets the value of the specified local variable in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69999-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69999-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariable (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69999-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="69999-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="69999-106">[in] Index lokální proměnné do tohoto rámce zásobníku jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="69999-106">[in] The index of the local variable in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="69999-107">[out] Ukazatel na adresu ICorDebugValue objekt, který představuje načtené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="69999-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69999-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="69999-108">Remarks</span></span>  
 <span data-ttu-id="69999-109">`GetLocalVariable` Metodu je možné použít v rámci zásobníku jazyka MSIL nebo v rámci kompilované just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="69999-109">The `GetLocalVariable` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69999-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="69999-110">Requirements</span></span>  
 <span data-ttu-id="69999-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69999-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69999-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69999-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69999-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69999-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69999-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69999-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
