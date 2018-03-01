---
title: "ICorDebugAssembly::EnumerateModules – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugAssembly.EnumerateModules
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::EnumerateModules
helpviewer_keywords:
- ICorDebugAssembly::EnumerateModules method [.NET Framework debugging]
- EnumerateModules method [.NET Framework debugging]
ms.assetid: c7ba51a1-0dd5-4452-b471-232febe0f897
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e5bc6aced78d1d7ffc6521bca52bed1b2e232bbe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugassemblyenumeratemodules-method"></a><span data-ttu-id="af80e-102">ICorDebugAssembly::EnumerateModules – metoda</span><span class="sxs-lookup"><span data-stu-id="af80e-102">ICorDebugAssembly::EnumerateModules Method</span></span>
<span data-ttu-id="af80e-103">Získá enumerátor pro moduly, které jsou součástí `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="af80e-103">Gets an enumerator for the modules contained in the `ICorDebugAssembly`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af80e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af80e-104">Syntax</span></span>  
  
```  
HRESULT EnumerateModules (  
    [out] ICorDebugModuleEnum **ppModules  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="af80e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="af80e-105">Parameters</span></span>  
 `ppModules`  
 <span data-ttu-id="af80e-106">[out] Ukazatel na adresu ICorDebugModuleEnum rozhraní, které je enumerátor.</span><span class="sxs-lookup"><span data-stu-id="af80e-106">[out] A pointer to the address of the ICorDebugModuleEnum interface that is the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af80e-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="af80e-107">Requirements</span></span>  
 <span data-ttu-id="af80e-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af80e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af80e-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="af80e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af80e-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af80e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af80e-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af80e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
