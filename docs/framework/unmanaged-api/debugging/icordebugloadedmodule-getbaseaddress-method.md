---
title: Metoda ICorDebugLoadedModule::GetBaseAddress
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e84d6deca0cd09cc547636007208c70ab91c1ab1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223534"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="e6ae4-102">Metoda ICorDebugLoadedModule::GetBaseAddress</span><span class="sxs-lookup"><span data-stu-id="e6ae4-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="e6ae4-103">Získá základní adresu načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="e6ae4-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6ae4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6ae4-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6ae4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e6ae4-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="e6ae4-106">[out] Ukazatel na základní adresa načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="e6ae4-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6ae4-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e6ae4-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e6ae4-108">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e6ae4-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6ae4-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e6ae4-109">Requirements</span></span>  
 <span data-ttu-id="e6ae4-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6ae4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6ae4-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e6ae4-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e6ae4-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6ae4-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e6ae4-113">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e6ae4-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e6ae4-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e6ae4-114">See also</span></span>

- [<span data-ttu-id="e6ae4-115">Rozhraní ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="e6ae4-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="e6ae4-116">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e6ae4-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
