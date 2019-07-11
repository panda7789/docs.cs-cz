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
ms.openlocfilehash: 29fc1b491aa4e340c3d8ad6f761d0d6d901649ac
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758560"
---
# <a name="icordebugilframegetlocalvariable-method"></a><span data-ttu-id="a2c5f-102">ICorDebugILFrame::GetLocalVariable – metoda</span><span class="sxs-lookup"><span data-stu-id="a2c5f-102">ICorDebugILFrame::GetLocalVariable Method</span></span>
<span data-ttu-id="a2c5f-103">Získá hodnotu místní proměnné zadané v tomto bloku zásobníku Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="a2c5f-103">Gets the value of the specified local variable in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2c5f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2c5f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariable (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2c5f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a2c5f-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="a2c5f-106">[in] Index lokální proměnné do tohoto rámce zásobníku jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="a2c5f-106">[in] The index of the local variable in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="a2c5f-107">[out] Ukazatel na adresu ICorDebugValue objekt, který představuje načtené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a2c5f-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2c5f-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a2c5f-108">Remarks</span></span>  
 <span data-ttu-id="a2c5f-109">`GetLocalVariable` Metodu je možné použít v rámci zásobníku jazyka MSIL nebo v rámci kompilované just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="a2c5f-109">The `GetLocalVariable` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2c5f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a2c5f-110">Requirements</span></span>  
 <span data-ttu-id="a2c5f-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2c5f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2c5f-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a2c5f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2c5f-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2c5f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2c5f-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2c5f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
