---
title: ICorDebugModule::GetAssembly – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetAssembly
helpviewer_keywords:
- ICorDebugModule::GetAssembly method [.NET Framework debugging]
- GetAssembly method [.NET Framework debugging]
ms.assetid: 989762c4-3d15-4485-b8ee-69e0fa8ec895
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ee602c85a2f591365d40984184780f70e8532bf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762700"
---
# <a name="icordebugmodulegetassembly-method"></a><span data-ttu-id="073e6-102">ICorDebugModule::GetAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="073e6-102">ICorDebugModule::GetAssembly Method</span></span>
<span data-ttu-id="073e6-103">Získá obsahující sestavení pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="073e6-103">Gets the containing assembly for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="073e6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="073e6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssembly(  
    [out] ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="073e6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="073e6-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="073e6-106">[out] Ukazatel na objekt icordebugassembly –, který představuje sestavení obsahující tento modul.</span><span class="sxs-lookup"><span data-stu-id="073e6-106">[out] A pointer to an ICorDebugAssembly object that represents the assembly containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="073e6-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="073e6-107">Requirements</span></span>  
 <span data-ttu-id="073e6-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="073e6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="073e6-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="073e6-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="073e6-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="073e6-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="073e6-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="073e6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
