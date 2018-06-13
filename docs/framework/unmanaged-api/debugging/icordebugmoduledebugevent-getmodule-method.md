---
title: ICorDebugModuleDebugEvent::GetModule – metoda
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 56ce5b3f5fb3c6d2a00c407afc303895273c2251
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419486"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="4a55b-102">ICorDebugModuleDebugEvent::GetModule – metoda</span><span class="sxs-lookup"><span data-stu-id="4a55b-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>
<span data-ttu-id="4a55b-103">Získá sloučené modul, který byl právě nenačetl nebo je odpojen.</span><span class="sxs-lookup"><span data-stu-id="4a55b-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a55b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a55b-104">Syntax</span></span>  
  
```  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4a55b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4a55b-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="4a55b-106">[out] Ukazatel na adresu ICorDebugModule objekt, který reprezentuje sloučené modul, který byl právě načten nebo odpojeno.</span><span class="sxs-lookup"><span data-stu-id="4a55b-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a55b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4a55b-107">Remarks</span></span>  
 <span data-ttu-id="4a55b-108">Můžete volat [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) metoda k určení, zda modul byl načten nebo odpojeno.</span><span class="sxs-lookup"><span data-stu-id="4a55b-108">You can call the [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a55b-109">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="4a55b-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a55b-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4a55b-110">Requirements</span></span>  
 <span data-ttu-id="4a55b-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a55b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a55b-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a55b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a55b-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a55b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a55b-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a55b-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a55b-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="4a55b-115">See Also</span></span>  
 [<span data-ttu-id="4a55b-116">ICorDebugModuleDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4a55b-116">ICorDebugModuleDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
 [<span data-ttu-id="4a55b-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="4a55b-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
