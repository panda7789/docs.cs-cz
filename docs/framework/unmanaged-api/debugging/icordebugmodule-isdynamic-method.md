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
ms.openlocfilehash: 45b1d0c0a3199227ab644ba8732198dd14b1cb4c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793000"
---
# <a name="icordebugmoduleisdynamic-method"></a><span data-ttu-id="7000b-102">ICorDebugModule::IsDynamic – metoda</span><span class="sxs-lookup"><span data-stu-id="7000b-102">ICorDebugModule::IsDynamic Method</span></span>
<span data-ttu-id="7000b-103">Načte hodnotu, která označuje, jestli je tento modul dynamický.</span><span class="sxs-lookup"><span data-stu-id="7000b-103">Gets a value that indicates whether this module is dynamic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7000b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7000b-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7000b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7000b-105">Parameters</span></span>  
 `pDynamic`  
 <span data-ttu-id="7000b-106">[out] `true`, pokud je tento modul dynamický; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="7000b-106">[out] `true` if this module is dynamic; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7000b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7000b-107">Remarks</span></span>  
 <span data-ttu-id="7000b-108">Dynamický modul může přidat nové třídy a odstranit existující třídy i poté, co byl modul načten.</span><span class="sxs-lookup"><span data-stu-id="7000b-108">A dynamic module can add new classes and delete existing classes even after the module has been loaded.</span></span> <span data-ttu-id="7000b-109">Zpětná volání [ICorDebugManagedCallback:: LoadClass –](icordebugmanagedcallback-loadclass-method.md) a [ICorDebugManagedCallback:: UnloadClass –](icordebugmanagedcallback-unloadclass-method.md) informují ladicí program, když byla třída přidána nebo odstraněna.</span><span class="sxs-lookup"><span data-stu-id="7000b-109">The [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks inform the debugger when a class has been added or deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7000b-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7000b-110">Requirements</span></span>  
 <span data-ttu-id="7000b-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7000b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7000b-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7000b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7000b-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7000b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7000b-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7000b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
