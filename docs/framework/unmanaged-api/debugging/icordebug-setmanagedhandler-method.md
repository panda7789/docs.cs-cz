---
title: ICorDebug::SetManagedHandler – metoda
ms.date: 03/30/2017
api_name:
- ICorDebug.SetManagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetManagedHandler
helpviewer_keywords:
- ICorDebug::SetManagedHandler method [.NET Framework debugging]
- SetManagedHandler method [.NET Framework debugging]
ms.assetid: d079131b-685b-4869-95be-826b88d28bd2
topic_type:
- apiref
ms.openlocfilehash: 54ef1cab27a39de39b39996729be6b8160570745
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788972"
---
# <a name="icordebugsetmanagedhandler-method"></a><span data-ttu-id="157f8-102">ICorDebug::SetManagedHandler – metoda</span><span class="sxs-lookup"><span data-stu-id="157f8-102">ICorDebug::SetManagedHandler Method</span></span>
<span data-ttu-id="157f8-103">Určuje objekt obslužné rutiny události pro spravované události.</span><span class="sxs-lookup"><span data-stu-id="157f8-103">Specifies the event handler object for managed events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="157f8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="157f8-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="157f8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="157f8-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="157f8-106">pro Ukazatel na objekt [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) , který je objektem obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="157f8-106">[in] A pointer to an [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) object, which is the event handler object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="157f8-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="157f8-107">Remarks</span></span>  
 <span data-ttu-id="157f8-108">`SetManagedHandler` musí být volána při vytváření.</span><span class="sxs-lookup"><span data-stu-id="157f8-108">`SetManagedHandler` must be called at creation time.</span></span>  
  
 <span data-ttu-id="157f8-109">Pokud implementace `ICorDebugManagedCallback` neobsahuje dostatečná rozhraní pro zpracování událostí ladění pro aplikaci, která je právě laděna, `SetManagedHandler` vrátí hodnotu HRESULT E_NOINTERFACE.</span><span class="sxs-lookup"><span data-stu-id="157f8-109">If the `ICorDebugManagedCallback` implementation does not contain sufficient interfaces to handle debugging events for the application that is being debugged, `SetManagedHandler` returns an HRESULT of E_NOINTERFACE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="157f8-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="157f8-110">Requirements</span></span>  
 <span data-ttu-id="157f8-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="157f8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="157f8-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="157f8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="157f8-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="157f8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="157f8-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="157f8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="157f8-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="157f8-115">See also</span></span>

- [<span data-ttu-id="157f8-116">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="157f8-116">ICorDebug Interface</span></span>](icordebug-interface.md)
