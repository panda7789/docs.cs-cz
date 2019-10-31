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
ms.openlocfilehash: 85f06b49aab1f1d1745bd7e359ed311c2ba1e44d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130981"
---
# <a name="icordebugilframegetlocalvariable-method"></a><span data-ttu-id="d65df-102">ICorDebugILFrame::GetLocalVariable – metoda</span><span class="sxs-lookup"><span data-stu-id="d65df-102">ICorDebugILFrame::GetLocalVariable Method</span></span>
<span data-ttu-id="d65df-103">Získá hodnotu zadané místní proměnné v rámci tohoto rámce zásobníku jazyka MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="d65df-103">Gets the value of the specified local variable in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d65df-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d65df-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariable (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d65df-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d65df-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="d65df-106">pro Index místní proměnné v tomto snímku zásobníku MSIL.</span><span class="sxs-lookup"><span data-stu-id="d65df-106">[in] The index of the local variable in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="d65df-107">mimo Ukazatel na adresu objektu ICorDebugValue, který představuje načtenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d65df-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d65df-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d65df-108">Remarks</span></span>  
 <span data-ttu-id="d65df-109">Metodu `GetLocalVariable` lze použít buď v rámci rámce zásobníku MSIL, nebo v kompilovaném snímku JIT (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="d65df-109">The `GetLocalVariable` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d65df-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d65df-110">Requirements</span></span>  
 <span data-ttu-id="d65df-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d65df-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d65df-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d65df-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d65df-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d65df-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d65df-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d65df-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
