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
ms.openlocfilehash: 4517f266bbb500223214a6a8fe5881e8b29566c3
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206887"
---
# <a name="icordebugmoduleisdynamic-method"></a><span data-ttu-id="04825-102">ICorDebugModule::IsDynamic – metoda</span><span class="sxs-lookup"><span data-stu-id="04825-102">ICorDebugModule::IsDynamic Method</span></span>
<span data-ttu-id="04825-103">Načte hodnotu, která označuje, jestli je tento modul dynamický.</span><span class="sxs-lookup"><span data-stu-id="04825-103">Gets a value that indicates whether this module is dynamic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04825-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04825-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04825-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="04825-105">Parameters</span></span>  
 `pDynamic`  
 <span data-ttu-id="04825-106">[out] `true` Pokud je tento modul dynamický; v opačném případě `false` .</span><span class="sxs-lookup"><span data-stu-id="04825-106">[out] `true` if this module is dynamic; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04825-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="04825-107">Remarks</span></span>  
 <span data-ttu-id="04825-108">Dynamický modul může přidat nové třídy a odstranit existující třídy i poté, co byl modul načten.</span><span class="sxs-lookup"><span data-stu-id="04825-108">A dynamic module can add new classes and delete existing classes even after the module has been loaded.</span></span> <span data-ttu-id="04825-109">Zpětná volání [ICorDebugManagedCallback:: LoadClass –](icordebugmanagedcallback-loadclass-method.md) a [ICorDebugManagedCallback:: UnloadClass –](icordebugmanagedcallback-unloadclass-method.md) informují ladicí program, když byla třída přidána nebo odstraněna.</span><span class="sxs-lookup"><span data-stu-id="04825-109">The [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks inform the debugger when a class has been added or deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04825-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="04825-110">Requirements</span></span>  
 <span data-ttu-id="04825-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04825-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04825-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="04825-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04825-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="04825-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04825-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04825-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
