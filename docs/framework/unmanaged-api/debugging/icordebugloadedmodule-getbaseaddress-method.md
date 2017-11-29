---
title: Metoda ICorDebugLoadedModule::GetBaseAddress
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b192c606697896371202e98945f83623bbb99bb9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="ce000-102">Metoda ICorDebugLoadedModule::GetBaseAddress</span><span class="sxs-lookup"><span data-stu-id="ce000-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="ce000-103">Získá základní adresu načíst modulu.</span><span class="sxs-lookup"><span data-stu-id="ce000-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce000-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce000-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ce000-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce000-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="ce000-106">[out] Ukazatel na základní adresu načíst modul.</span><span class="sxs-lookup"><span data-stu-id="ce000-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce000-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ce000-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ce000-108">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="ce000-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce000-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ce000-109">Requirements</span></span>  
 <span data-ttu-id="ce000-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce000-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce000-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ce000-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce000-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce000-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce000-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce000-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce000-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce000-114">See Also</span></span>  
 [<span data-ttu-id="ce000-115">Rozhraní ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="ce000-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="ce000-116">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="ce000-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
