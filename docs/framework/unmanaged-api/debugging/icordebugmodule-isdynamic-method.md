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
ms.openlocfilehash: 5157c62f2719a9d62608750cd122561807197494
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418291"
---
# <a name="icordebugmoduleisdynamic-method"></a><span data-ttu-id="f1505-102">ICorDebugModule::IsDynamic – metoda</span><span class="sxs-lookup"><span data-stu-id="f1505-102">ICorDebugModule::IsDynamic Method</span></span>
<span data-ttu-id="f1505-103">Získá hodnotu, která určuje, zda je tento modul dynamické.</span><span class="sxs-lookup"><span data-stu-id="f1505-103">Gets a value that indicates whether this module is dynamic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1505-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1505-104">Syntax</span></span>  
  
```  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f1505-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f1505-105">Parameters</span></span>  
 `pDynamic`  
 <span data-ttu-id="f1505-106">[out] `true` Pokud tento modul je dynamický; jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="f1505-106">[out] `true` if this module is dynamic; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1505-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f1505-107">Remarks</span></span>  
 <span data-ttu-id="f1505-108">Modul dynamická můžete přidat nové třídy a odstranit existující třídy, i když se načetl modul.</span><span class="sxs-lookup"><span data-stu-id="f1505-108">A dynamic module can add new classes and delete existing classes even after the module has been loaded.</span></span> <span data-ttu-id="f1505-109">[Icordebugmanagedcallback::loadclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) a [icordebugmanagedcallback::unloadclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) zpětná volání informovat ladicí program, když přidat nebo odstranit třídy.</span><span class="sxs-lookup"><span data-stu-id="f1505-109">The [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks inform the debugger when a class has been added or deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1505-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f1505-110">Requirements</span></span>  
 <span data-ttu-id="f1505-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1505-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1505-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f1505-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1505-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1505-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1505-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1505-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
