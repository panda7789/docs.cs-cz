---
title: ICorDebugAssembly::EnumerateModules – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1d8d76084bcf0b5951c6431c6f21f352406050b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737367"
---
# <a name="icordebugassemblyenumeratemodules-method"></a><span data-ttu-id="dbdf7-102">ICorDebugAssembly::EnumerateModules – metoda</span><span class="sxs-lookup"><span data-stu-id="dbdf7-102">ICorDebugAssembly::EnumerateModules Method</span></span>
<span data-ttu-id="dbdf7-103">Získá enumerátor pro moduly, které jsou součástí `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="dbdf7-103">Gets an enumerator for the modules contained in the `ICorDebugAssembly`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbdf7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dbdf7-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateModules (  
    [out] ICorDebugModuleEnum **ppModules  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dbdf7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dbdf7-105">Parameters</span></span>  
 `ppModules`  
 <span data-ttu-id="dbdf7-106">[out] Ukazatel na adresu icordebugmoduleenum – rozhraní, která je enumerátor.</span><span class="sxs-lookup"><span data-stu-id="dbdf7-106">[out] A pointer to the address of the ICorDebugModuleEnum interface that is the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbdf7-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dbdf7-107">Requirements</span></span>  
 <span data-ttu-id="dbdf7-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbdf7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbdf7-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dbdf7-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dbdf7-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dbdf7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dbdf7-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbdf7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
