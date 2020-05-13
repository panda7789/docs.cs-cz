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
ms.openlocfilehash: d715f5842bb7f75da5311d34bf7d4596f0801a92
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210277"
---
# <a name="icordebugilframegetargument-method"></a><span data-ttu-id="3ccf6-102">ICorDebugILFrame::GetArgument – metoda</span><span class="sxs-lookup"><span data-stu-id="3ccf6-102">ICorDebugILFrame::GetArgument Method</span></span>
<span data-ttu-id="3ccf6-103">Získá hodnotu zadaného argumentu v rámci tohoto rámce zásobníku jazyka MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="3ccf6-103">Gets the value of the specified argument in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ccf6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ccf6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArgument (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ccf6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3ccf6-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="3ccf6-106">pro Index argumentu v tomto snímku zásobníku MSIL.</span><span class="sxs-lookup"><span data-stu-id="3ccf6-106">[in] The index of the argument in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="3ccf6-107">mimo Ukazatel na adresu objektu ICorDebugValue, který představuje načtenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3ccf6-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ccf6-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3ccf6-108">Remarks</span></span>  
 <span data-ttu-id="3ccf6-109">Tuto `GetArgument` metodu lze použít buď v rámci zásobníku MSIL, nebo v kompilovaném rámci JIT (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="3ccf6-109">The `GetArgument` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ccf6-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3ccf6-110">Requirements</span></span>  
 <span data-ttu-id="3ccf6-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ccf6-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ccf6-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3ccf6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3ccf6-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3ccf6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ccf6-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ccf6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
