---
title: ICorDebugBreakpoint::Activate – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint.Activate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint::Activate
helpviewer_keywords:
- ICorDebugBreakpoint::Activate method [.NET Framework debugging]
- Activate method [.NET Framework debugging]
ms.assetid: e30c29f7-3f19-4081-b572-a731aa14cd44
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82dad6af545464baade2b82d65e7ad4dba19fe3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402337"
---
# <a name="icordebugbreakpointactivate-method"></a><span data-ttu-id="3d92c-102">ICorDebugBreakpoint::Activate – metoda</span><span class="sxs-lookup"><span data-stu-id="3d92c-102">ICorDebugBreakpoint::Activate Method</span></span>
<span data-ttu-id="3d92c-103">Nastaví aktivní stav tohoto `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="3d92c-103">Sets the active state of this `ICorDebugBreakpoint`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d92c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d92c-104">Syntax</span></span>  
  
```  
HRESULT Activate (  
    [in] BOOL bActive  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3d92c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3d92c-105">Parameters</span></span>  
 `bActive`  
 <span data-ttu-id="3d92c-106">[v] Nastavte tuto hodnotu na `true` k určení stavu jako aktivní; jinak, nastavte tuto hodnotu na `false`.</span><span class="sxs-lookup"><span data-stu-id="3d92c-106">[in] Set this value to `true` to specify the state as active; otherwise, set this value to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d92c-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3d92c-107">Requirements</span></span>  
 <span data-ttu-id="3d92c-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d92c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d92c-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d92c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d92c-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d92c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d92c-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d92c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
