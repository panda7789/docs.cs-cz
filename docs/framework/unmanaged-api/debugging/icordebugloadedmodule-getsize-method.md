---
title: Metoda ICorDebugLoadedModule::GetSize
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3067cdee1d3a5df0ad5594bce581139431fd1846
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936877"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="e745c-102">Metoda ICorDebugLoadedModule::GetSize</span><span class="sxs-lookup"><span data-stu-id="e745c-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="e745c-103">Získá velikost načteného modulu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="e745c-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e745c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e745c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e745c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e745c-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="e745c-106">mimo Ukazatel na počet bajtů v načteném modulu.</span><span class="sxs-lookup"><span data-stu-id="e745c-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e745c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e745c-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e745c-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e745c-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e745c-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e745c-109">Requirements</span></span>  
 <span data-ttu-id="e745c-110">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e745c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e745c-111">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e745c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e745c-112">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e745c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e745c-113">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e745c-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e745c-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e745c-114">See also</span></span>

- [<span data-ttu-id="e745c-115">ICorDebugLoadedModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e745c-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="e745c-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e745c-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
