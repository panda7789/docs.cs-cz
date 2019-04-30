---
title: Metoda ICorDebugLoadedModule::GetSize
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4601261971cce32b6d6d9ee7377f725a85103a1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946247"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="298bd-102">Metoda ICorDebugLoadedModule::GetSize</span><span class="sxs-lookup"><span data-stu-id="298bd-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="298bd-103">Získá velikost v bajtech načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="298bd-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="298bd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="298bd-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="298bd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="298bd-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="298bd-106">[out] Ukazatel na počet bajtů v načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="298bd-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="298bd-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="298bd-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="298bd-108">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="298bd-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="298bd-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="298bd-109">Requirements</span></span>  
 <span data-ttu-id="298bd-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="298bd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="298bd-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="298bd-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="298bd-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="298bd-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="298bd-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="298bd-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="298bd-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="298bd-114">See also</span></span>

- [<span data-ttu-id="298bd-115">ICorDebugLoadedModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="298bd-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="298bd-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="298bd-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
