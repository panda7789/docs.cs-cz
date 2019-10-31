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
ms.openlocfilehash: 5774b40178ce0d7c2ef5d063a37b9011fc2630df
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127953"
---
# <a name="icordebugmoduleisdynamic-method"></a><span data-ttu-id="3557f-102">ICorDebugModule::IsDynamic – metoda</span><span class="sxs-lookup"><span data-stu-id="3557f-102">ICorDebugModule::IsDynamic Method</span></span>
<span data-ttu-id="3557f-103">Načte hodnotu, která označuje, jestli je tento modul dynamický.</span><span class="sxs-lookup"><span data-stu-id="3557f-103">Gets a value that indicates whether this module is dynamic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3557f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3557f-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3557f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3557f-105">Parameters</span></span>  
 `pDynamic`  
 <span data-ttu-id="3557f-106">[out] `true`, pokud je tento modul dynamický; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="3557f-106">[out] `true` if this module is dynamic; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3557f-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3557f-107">Remarks</span></span>  
 <span data-ttu-id="3557f-108">Dynamický modul může přidat nové třídy a odstranit existující třídy i poté, co byl modul načten.</span><span class="sxs-lookup"><span data-stu-id="3557f-108">A dynamic module can add new classes and delete existing classes even after the module has been loaded.</span></span> <span data-ttu-id="3557f-109">Zpětná volání [ICorDebugManagedCallback:: LoadClass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) a [ICorDebugManagedCallback:: UnloadClass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) informují ladicí program, když byla třída přidána nebo odstraněna.</span><span class="sxs-lookup"><span data-stu-id="3557f-109">The [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks inform the debugger when a class has been added or deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3557f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3557f-110">Requirements</span></span>  
 <span data-ttu-id="3557f-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3557f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3557f-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3557f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3557f-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3557f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3557f-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3557f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
