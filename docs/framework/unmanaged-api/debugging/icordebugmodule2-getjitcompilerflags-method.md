---
title: ICorDebugModule2::GetJITCompilerFlags – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.GetJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::GetJITCompilerFlags
helpviewer_keywords:
- GetJITCompilerFlags method [.NET Framework debugging]
- ICorDebugModule2::GetJITCompilerFlags method [.NET Framework debugging]
ms.assetid: 7212d9f4-989b-44e3-b8d4-ffc35922f6a0
topic_type:
- apiref
ms.openlocfilehash: 6af5bc22616be196be7fdb0d417800d631d87506
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213644"
---
# <a name="icordebugmodule2getjitcompilerflags-method"></a><span data-ttu-id="28d36-102">ICorDebugModule2::GetJITCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="28d36-102">ICorDebugModule2::GetJITCompilerFlags Method</span></span>
<span data-ttu-id="28d36-103">Získá příznaky, které řídí kompilaci JIT (just-in-time) tohoto ICorDebugModule2.</span><span class="sxs-lookup"><span data-stu-id="28d36-103">Gets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28d36-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28d36-104">Syntax</span></span>  
  
```cpp  
HRESULT GetJITCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28d36-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="28d36-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="28d36-106">mimo Ukazatel na hodnotu výčtu [CorDebugJITCompilerFlags –](cordebugjitcompilerflags-enumeration.md) , která řídí kompilaci JIT.</span><span class="sxs-lookup"><span data-stu-id="28d36-106">[out] A pointer to a value of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration that controls the JIT compilation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28d36-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="28d36-107">Requirements</span></span>  
 <span data-ttu-id="28d36-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28d36-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28d36-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="28d36-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="28d36-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="28d36-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28d36-111">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28d36-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
