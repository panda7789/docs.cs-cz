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
ms.openlocfilehash: b55bd41039fce84a21c5d651d93b56f5d84b7611
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088183"
---
# <a name="icordebugassemblyenumeratemodules-method"></a><span data-ttu-id="333b9-102">ICorDebugAssembly::EnumerateModules – metoda</span><span class="sxs-lookup"><span data-stu-id="333b9-102">ICorDebugAssembly::EnumerateModules Method</span></span>
<span data-ttu-id="333b9-103">Získá enumerátor pro moduly obsažené v `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="333b9-103">Gets an enumerator for the modules contained in the `ICorDebugAssembly`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="333b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="333b9-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateModules (  
    [out] ICorDebugModuleEnum **ppModules  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="333b9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="333b9-105">Parameters</span></span>  
 `ppModules`  
 <span data-ttu-id="333b9-106">mimo Ukazatel na adresu rozhraní ICorDebugModuleEnum, které je enumerátorem.</span><span class="sxs-lookup"><span data-stu-id="333b9-106">[out] A pointer to the address of the ICorDebugModuleEnum interface that is the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="333b9-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="333b9-107">Requirements</span></span>  
 <span data-ttu-id="333b9-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="333b9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="333b9-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="333b9-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="333b9-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="333b9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="333b9-111">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="333b9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
