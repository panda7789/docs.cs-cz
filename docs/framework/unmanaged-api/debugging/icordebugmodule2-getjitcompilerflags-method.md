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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88277be93d3a0e445e97217655d3d524962dd01d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764230"
---
# <a name="icordebugmodule2getjitcompilerflags-method"></a><span data-ttu-id="86342-102">ICorDebugModule2::GetJITCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="86342-102">ICorDebugModule2::GetJITCompilerFlags Method</span></span>
<span data-ttu-id="86342-103">Získá příznaky, které řídí tento icordebugmodule2 – kompilace just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="86342-103">Gets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86342-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86342-104">Syntax</span></span>  
  
```cpp  
HRESULT GetJITCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86342-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="86342-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="86342-106">[out] Ukazatel na hodnotu [cordebugjitcompilerflags –](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) výčet, který určuje kompilaci JIT.</span><span class="sxs-lookup"><span data-stu-id="86342-106">[out] A pointer to a value of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration that controls the JIT compilation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86342-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="86342-107">Requirements</span></span>  
 <span data-ttu-id="86342-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86342-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86342-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86342-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86342-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86342-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86342-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86342-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
