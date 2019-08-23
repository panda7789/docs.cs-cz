---
title: 'ICorDebugModuleDebugEvent:: GetModule – metoda'
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e68fab11a881854ae4c3fe073f73150694d31ae5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965113"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="27cab-102">ICorDebugModuleDebugEvent:: GetModule – metoda</span><span class="sxs-lookup"><span data-stu-id="27cab-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>
<span data-ttu-id="27cab-103">Získá sloučený modul, který byl právě načten nebo uvolněn.</span><span class="sxs-lookup"><span data-stu-id="27cab-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27cab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27cab-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27cab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="27cab-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="27cab-106">mimo Ukazatel na adresu ICorDebugModule objektu, který reprezentuje sloučený modul, který byl právě načten nebo uvolněn.</span><span class="sxs-lookup"><span data-stu-id="27cab-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27cab-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="27cab-107">Remarks</span></span>  
 <span data-ttu-id="27cab-108">Můžete zavolat metodu [GetEventKind –](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) a zjistit, zda byl modul načten nebo uvolněn.</span><span class="sxs-lookup"><span data-stu-id="27cab-108">You can call the [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="27cab-109">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="27cab-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27cab-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="27cab-110">Requirements</span></span>  
 <span data-ttu-id="27cab-111">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27cab-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27cab-112">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="27cab-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="27cab-113">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27cab-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27cab-114">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27cab-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27cab-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="27cab-115">See also</span></span>

- [<span data-ttu-id="27cab-116">ICorDebugModuleDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="27cab-116">ICorDebugModuleDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)
- [<span data-ttu-id="27cab-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="27cab-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
