---
title: Metoda ICorDebugLoadedModule::GetBaseAddress
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5ef73be22ea79d15ec53e8ab33c34441002acce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732424"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="8b2a0-102">Metoda ICorDebugLoadedModule::GetBaseAddress</span><span class="sxs-lookup"><span data-stu-id="8b2a0-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="8b2a0-103">Získá základní adresu načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="8b2a0-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b2a0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b2a0-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8b2a0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b2a0-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="8b2a0-106">[out] Ukazatel na základní adresa načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="8b2a0-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b2a0-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8b2a0-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b2a0-108">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8b2a0-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b2a0-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8b2a0-109">Requirements</span></span>  
 <span data-ttu-id="8b2a0-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b2a0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b2a0-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b2a0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b2a0-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b2a0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b2a0-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b2a0-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b2a0-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b2a0-114">See also</span></span>
- [<span data-ttu-id="8b2a0-115">ICorDebugLoadedModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8b2a0-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="8b2a0-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="8b2a0-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
