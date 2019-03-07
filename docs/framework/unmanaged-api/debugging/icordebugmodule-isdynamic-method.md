---
title: ICorDebugModule::IsDynamic – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.IsDynamic
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsDynamic
helpviewer_keywords:
- IsDynamic method [.NET Framework debugging]
- ICorDebugModule::IsDynamic method [.NET Framework debugging]
ms.assetid: 5eefe716-5025-4a4c-970c-c823cdc7bb87
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8012d669cabc1bb589dcfe66bdf2e9b83dc5cb2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502446"
---
# <a name="icordebugmoduleisdynamic-method"></a><span data-ttu-id="5aa14-102">ICorDebugModule::IsDynamic – metoda</span><span class="sxs-lookup"><span data-stu-id="5aa14-102">ICorDebugModule::IsDynamic Method</span></span>
<span data-ttu-id="5aa14-103">Získá hodnotu, která určuje, zda tento modul je dynamická.</span><span class="sxs-lookup"><span data-stu-id="5aa14-103">Gets a value that indicates whether this module is dynamic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5aa14-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5aa14-104">Syntax</span></span>  
  
```  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5aa14-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5aa14-105">Parameters</span></span>  
 `pDynamic`  
 <span data-ttu-id="5aa14-106">[out] `true` Pokud tento modul je dynamický; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="5aa14-106">[out] `true` if this module is dynamic; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5aa14-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5aa14-107">Remarks</span></span>  
 <span data-ttu-id="5aa14-108">Dynamický modul můžete přidat nové třídy a odstranit existující třídy i po načtení modulu.</span><span class="sxs-lookup"><span data-stu-id="5aa14-108">A dynamic module can add new classes and delete existing classes even after the module has been loaded.</span></span> <span data-ttu-id="5aa14-109">[Icordebugmanagedcallback::loadclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) a [icordebugmanagedcallback::unloadclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) zpětná volání informovat ladicí program, když přidá nebo odstraní třídy.</span><span class="sxs-lookup"><span data-stu-id="5aa14-109">The [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks inform the debugger when a class has been added or deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5aa14-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5aa14-110">Requirements</span></span>  
 <span data-ttu-id="5aa14-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5aa14-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5aa14-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5aa14-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5aa14-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5aa14-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5aa14-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5aa14-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
