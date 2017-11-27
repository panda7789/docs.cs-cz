---
title: "ICorDebugModule2::GetJITCompilerFlags – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule2.GetJITCompilerFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule2::GetJITCompilerFlags
helpviewer_keywords:
- GetJITCompilerFlags method [.NET Framework debugging]
- ICorDebugModule2::GetJITCompilerFlags method [.NET Framework debugging]
ms.assetid: 7212d9f4-989b-44e3-b8d4-ffc35922f6a0
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0a158b779ad85b8161d6f6ea8bf2dc4c1db1a283
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodule2getjitcompilerflags-method"></a><span data-ttu-id="90941-102">ICorDebugModule2::GetJITCompilerFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="90941-102">ICorDebugModule2::GetJITCompilerFlags Method</span></span>
<span data-ttu-id="90941-103">Získá příznaky, které řídí tento ICorDebugModule2 kompilace v běhu (JIT).</span><span class="sxs-lookup"><span data-stu-id="90941-103">Gets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90941-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90941-104">Syntax</span></span>  
  
```  
HRESULT GetJITCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="90941-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="90941-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="90941-106">[out] Ukazatel na hodnotu [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) výčet, který řídí JIT – kompilace.</span><span class="sxs-lookup"><span data-stu-id="90941-106">[out] A pointer to a value of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration that controls the JIT compilation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90941-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="90941-107">Requirements</span></span>  
 <span data-ttu-id="90941-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90941-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90941-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="90941-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="90941-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90941-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90941-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90941-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
