---
title: ICorDebugModule::IsInMemory – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.IsInMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsInMemory
helpviewer_keywords:
- IsInMemory method [.NET Framework debugging]
- ICorDebugModule::IsInMemory method [.NET Framework debugging]
ms.assetid: 89940711-98e7-4aa6-bffc-5e39e91e1b7d
topic_type:
- apiref
ms.openlocfilehash: 1384acff4ea3d1aa820b065cd2c56f649f0cbdbb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127927"
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="57967-102">ICorDebugModule::IsInMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="57967-102">ICorDebugModule::IsInMemory Method</span></span>
<span data-ttu-id="57967-103">Načte hodnotu, která označuje, jestli tento modul existuje jenom v paměti.</span><span class="sxs-lookup"><span data-stu-id="57967-103">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57967-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57967-104">Syntax</span></span>  
  
```cpp  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57967-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="57967-105">Parameters</span></span>  
 `pInMemory`  
 <span data-ttu-id="57967-106">[out] `true`, jestli tento modul existuje jenom v paměti; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="57967-106">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57967-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="57967-107">Remarks</span></span>  
 <span data-ttu-id="57967-108">Modul CLR (Common Language Runtime) podporuje načítání modulů z nezpracovaných datových proudů bajtů.</span><span class="sxs-lookup"><span data-stu-id="57967-108">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="57967-109">Tyto moduly se nazývají *moduly v paměti* a neexistují na disku.</span><span class="sxs-lookup"><span data-stu-id="57967-109">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57967-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="57967-110">Requirements</span></span>  
 <span data-ttu-id="57967-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57967-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57967-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="57967-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="57967-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="57967-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57967-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57967-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57967-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="57967-115">See also</span></span>
