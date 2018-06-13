---
title: Metoda ICorDebugLoadedModule::GetBaseAddress
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c12ea84f1a706850972b2e404ec52eea3523de7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412633"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="84d67-102">Metoda ICorDebugLoadedModule::GetBaseAddress</span><span class="sxs-lookup"><span data-stu-id="84d67-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="84d67-103">Získá základní adresu načíst modulu.</span><span class="sxs-lookup"><span data-stu-id="84d67-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84d67-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84d67-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="84d67-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="84d67-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="84d67-106">[out] Ukazatel na základní adresu načíst modul.</span><span class="sxs-lookup"><span data-stu-id="84d67-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84d67-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="84d67-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="84d67-108">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="84d67-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84d67-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="84d67-109">Requirements</span></span>  
 <span data-ttu-id="84d67-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84d67-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84d67-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="84d67-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84d67-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84d67-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84d67-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84d67-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84d67-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="84d67-114">See Also</span></span>  
 [<span data-ttu-id="84d67-115">ICorDebugLoadedModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="84d67-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="84d67-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="84d67-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
