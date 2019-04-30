---
title: ICorDebugModuleDebugEvent::GetModule – metoda
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c0cc1305f47f03c8c9b35bab5c980cb23d1b157
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942490"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="15d67-102">ICorDebugModuleDebugEvent::GetModule – metoda</span><span class="sxs-lookup"><span data-stu-id="15d67-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>
<span data-ttu-id="15d67-103">Získá sloučené modul, který byl právě nenačetl nebo je uvolněna.</span><span class="sxs-lookup"><span data-stu-id="15d67-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15d67-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15d67-104">Syntax</span></span>  
  
```  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15d67-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="15d67-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="15d67-106">[out] Ukazatel na adresu icordebugmodule – objekt, který představuje sloučené modul, který byl právě načteny nebo uvolněny.</span><span class="sxs-lookup"><span data-stu-id="15d67-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15d67-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="15d67-107">Remarks</span></span>  
 <span data-ttu-id="15d67-108">Můžete volat [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) metodou ke zjištění, zda byl modul načten nebo byla uvolněna.</span><span class="sxs-lookup"><span data-stu-id="15d67-108">You can call the [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15d67-109">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="15d67-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15d67-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="15d67-110">Requirements</span></span>  
 <span data-ttu-id="15d67-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15d67-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15d67-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="15d67-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="15d67-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15d67-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15d67-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15d67-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15d67-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15d67-115">See also</span></span>

- [<span data-ttu-id="15d67-116">ICorDebugModuleDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="15d67-116">ICorDebugModuleDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)
- [<span data-ttu-id="15d67-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="15d67-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
