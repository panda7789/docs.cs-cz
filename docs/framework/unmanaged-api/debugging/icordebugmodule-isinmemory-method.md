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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 223989d883c421be228fb3d6a608643a5246c060
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763709"
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="39f0c-102">ICorDebugModule::IsInMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="39f0c-102">ICorDebugModule::IsInMemory Method</span></span>
<span data-ttu-id="39f0c-103">Získá hodnotu, která označuje, zda tento modul existuje pouze v paměti.</span><span class="sxs-lookup"><span data-stu-id="39f0c-103">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39f0c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39f0c-104">Syntax</span></span>  
  
```cpp  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39f0c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="39f0c-105">Parameters</span></span>  
 `pInMemory`  
 <span data-ttu-id="39f0c-106">[out] `true` Pokud tento modul existuje pouze v paměti; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="39f0c-106">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39f0c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="39f0c-107">Remarks</span></span>  
 <span data-ttu-id="39f0c-108">Modul CLR (CLR) podporuje načítání modulů z nezpracované datové proudy bajtů.</span><span class="sxs-lookup"><span data-stu-id="39f0c-108">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="39f0c-109">Tyto moduly se nazývají *moduly v paměti* a neexistuje na disku.</span><span class="sxs-lookup"><span data-stu-id="39f0c-109">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39f0c-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="39f0c-110">Requirements</span></span>  
 <span data-ttu-id="39f0c-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39f0c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39f0c-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="39f0c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39f0c-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39f0c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39f0c-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39f0c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39f0c-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="39f0c-115">See also</span></span>
