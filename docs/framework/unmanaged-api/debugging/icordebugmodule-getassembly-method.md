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
ms.openlocfilehash: 29c9d9dde4776ef729c0bbae7b644171a265e3ec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137470"
---
# <a name="icordebugmodulegetassembly-method"></a><span data-ttu-id="7e581-102">ICorDebugModule::GetAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="7e581-102">ICorDebugModule::GetAssembly Method</span></span>
<span data-ttu-id="7e581-103">Získá nadřazené sestavení pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="7e581-103">Gets the containing assembly for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e581-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e581-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssembly(  
    [out] ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e581-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7e581-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="7e581-106">mimo Ukazatel na objekt ICorDebugAssembly, který představuje sestavení obsahující tento modul.</span><span class="sxs-lookup"><span data-stu-id="7e581-106">[out] A pointer to an ICorDebugAssembly object that represents the assembly containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e581-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7e581-107">Requirements</span></span>  
 <span data-ttu-id="7e581-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e581-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e581-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7e581-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e581-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7e581-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e581-111">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e581-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
