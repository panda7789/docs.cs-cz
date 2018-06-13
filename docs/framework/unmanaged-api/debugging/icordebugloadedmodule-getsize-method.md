---
title: Metoda ICorDebugLoadedModule::GetSize
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9768fb91749158bf3193919b2106bde1c618468a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413228"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="9ed7a-102">Metoda ICorDebugLoadedModule::GetSize</span><span class="sxs-lookup"><span data-stu-id="9ed7a-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="9ed7a-103">Získá velikost v bajtech načíst modul.</span><span class="sxs-lookup"><span data-stu-id="9ed7a-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ed7a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ed7a-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9ed7a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9ed7a-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="9ed7a-106">[out] Ukazatel na počet bajtů v modulu načíst.</span><span class="sxs-lookup"><span data-stu-id="9ed7a-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ed7a-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9ed7a-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ed7a-108">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="9ed7a-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ed7a-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9ed7a-109">Requirements</span></span>  
 <span data-ttu-id="9ed7a-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ed7a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ed7a-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ed7a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ed7a-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ed7a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ed7a-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ed7a-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ed7a-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="9ed7a-114">See Also</span></span>  
 [<span data-ttu-id="9ed7a-115">ICorDebugLoadedModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9ed7a-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="9ed7a-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="9ed7a-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
