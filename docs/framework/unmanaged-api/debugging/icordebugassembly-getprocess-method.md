---
title: ICorDebugAssembly::GetProcess – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetProcess
helpviewer_keywords:
- ICorDebugAssembly::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: ea52be06-0a16-4f57-afca-4287d72e76c4
topic_type:
- apiref
ms.openlocfilehash: 49b234b065eb66dc2ec0bc7e991117c5b54a92f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73196350"
---
# <a name="icordebugassemblygetprocess-method"></a><span data-ttu-id="a505c-102">ICorDebugAssembly::GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="a505c-102">ICorDebugAssembly::GetProcess Method</span></span>
<span data-ttu-id="a505c-103">Načte ukazatel rozhraní na proces, ve kterém je spuštěná tato instance ICorDebugAssembly.</span><span class="sxs-lookup"><span data-stu-id="a505c-103">Gets an interface pointer to the process in which this ICorDebugAssembly instance is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a505c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a505c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a505c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a505c-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="a505c-106">mimo Ukazatel na rozhraní ICorDebugProcess, které představuje proces.</span><span class="sxs-lookup"><span data-stu-id="a505c-106">[out] A pointer to an ICorDebugProcess interface that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a505c-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a505c-107">Requirements</span></span>  
 <span data-ttu-id="a505c-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a505c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a505c-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a505c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a505c-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a505c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a505c-111">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a505c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
