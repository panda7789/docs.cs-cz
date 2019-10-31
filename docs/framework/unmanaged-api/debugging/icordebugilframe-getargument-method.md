---
title: ICorDebugILFrame::GetArgument – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetArgument
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetArgument
helpviewer_keywords:
- GetArgument method [.NET Framework debugging]
- ICorDebugILFrame::GetArgument method [.NET Framework debugging]
ms.assetid: 4e2fd423-f643-4c27-ba5f-41b5ebc3b416
topic_type:
- apiref
ms.openlocfilehash: 01c7cb2e4359a477c26f995602dbf29668e567c0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131011"
---
# <a name="icordebugilframegetargument-method"></a><span data-ttu-id="c86c2-102">ICorDebugILFrame::GetArgument – metoda</span><span class="sxs-lookup"><span data-stu-id="c86c2-102">ICorDebugILFrame::GetArgument Method</span></span>
<span data-ttu-id="c86c2-103">Získá hodnotu zadaného argumentu v rámci tohoto rámce zásobníku jazyka MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="c86c2-103">Gets the value of the specified argument in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c86c2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c86c2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArgument (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c86c2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c86c2-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="c86c2-106">pro Index argumentu v tomto snímku zásobníku MSIL.</span><span class="sxs-lookup"><span data-stu-id="c86c2-106">[in] The index of the argument in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="c86c2-107">mimo Ukazatel na adresu objektu ICorDebugValue, který představuje načtenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c86c2-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c86c2-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c86c2-108">Remarks</span></span>  
 <span data-ttu-id="c86c2-109">Metodu `GetArgument` lze použít buď v rámci rámce zásobníku MSIL, nebo v kompilovaném snímku JIT (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="c86c2-109">The `GetArgument` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c86c2-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c86c2-110">Requirements</span></span>  
 <span data-ttu-id="c86c2-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c86c2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c86c2-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c86c2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c86c2-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c86c2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c86c2-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c86c2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
