---
title: "ICorDebugModule::IsDynamic – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.IsDynamic
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::IsDynamic
helpviewer_keywords:
- IsDynamic method [.NET Framework debugging]
- ICorDebugModule::IsDynamic method [.NET Framework debugging]
ms.assetid: 5eefe716-5025-4a4c-970c-c823cdc7bb87
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e3583749ddb48015b43d45061d3e4cb10e08016b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmoduleisdynamic-method"></a><span data-ttu-id="ef8e4-102">ICorDebugModule::IsDynamic – metoda</span><span class="sxs-lookup"><span data-stu-id="ef8e4-102">ICorDebugModule::IsDynamic Method</span></span>
<span data-ttu-id="ef8e4-103">Získá hodnotu, která určuje, zda je tento modul dynamické.</span><span class="sxs-lookup"><span data-stu-id="ef8e4-103">Gets a value that indicates whether this module is dynamic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef8e4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef8e4-104">Syntax</span></span>  
  
```  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ef8e4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ef8e4-105">Parameters</span></span>  
 `pDynamic`  
 <span data-ttu-id="ef8e4-106">[out] `true` Pokud tento modul je dynamický; jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="ef8e4-106">[out] `true` if this module is dynamic; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef8e4-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ef8e4-107">Remarks</span></span>  
 <span data-ttu-id="ef8e4-108">Modul dynamická můžete přidat nové třídy a odstranit existující třídy, i když se načetl modul.</span><span class="sxs-lookup"><span data-stu-id="ef8e4-108">A dynamic module can add new classes and delete existing classes even after the module has been loaded.</span></span> <span data-ttu-id="ef8e4-109">[Icordebugmanagedcallback::loadclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) a [icordebugmanagedcallback::unloadclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) zpětná volání informovat ladicí program, když přidat nebo odstranit třídy.</span><span class="sxs-lookup"><span data-stu-id="ef8e4-109">The [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks inform the debugger when a class has been added or deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef8e4-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ef8e4-110">Requirements</span></span>  
 <span data-ttu-id="ef8e4-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef8e4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef8e4-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ef8e4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef8e4-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef8e4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef8e4-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef8e4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
