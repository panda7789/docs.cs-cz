---
title: Metoda ICorDebugLoadedModule::GetSize
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4c4888419bb13db43a4a15d98965cc8d3cb8e77
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54515576"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="0ebb8-102">Metoda ICorDebugLoadedModule::GetSize</span><span class="sxs-lookup"><span data-stu-id="0ebb8-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="0ebb8-103">Získá velikost v bajtech načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="0ebb8-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ebb8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ebb8-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0ebb8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0ebb8-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="0ebb8-106">[out] Ukazatel na počet bajtů v načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="0ebb8-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ebb8-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0ebb8-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0ebb8-108">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0ebb8-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ebb8-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0ebb8-109">Requirements</span></span>  
 <span data-ttu-id="0ebb8-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ebb8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ebb8-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0ebb8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ebb8-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ebb8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ebb8-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ebb8-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ebb8-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0ebb8-114">See also</span></span>
- [<span data-ttu-id="0ebb8-115">ICorDebugLoadedModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0ebb8-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="0ebb8-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0ebb8-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
