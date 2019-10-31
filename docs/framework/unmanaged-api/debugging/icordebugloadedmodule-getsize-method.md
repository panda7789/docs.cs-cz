---
title: Metoda ICorDebugLoadedModule::GetSize
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
ms.openlocfilehash: 3f2f8a1721847b8f7b845c42aa3c91e032c2d474
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122635"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="5cd71-102">Metoda ICorDebugLoadedModule::GetSize</span><span class="sxs-lookup"><span data-stu-id="5cd71-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="5cd71-103">Získá velikost načteného modulu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="5cd71-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cd71-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5cd71-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5cd71-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5cd71-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="5cd71-106">mimo Ukazatel na počet bajtů v načteném modulu.</span><span class="sxs-lookup"><span data-stu-id="5cd71-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5cd71-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5cd71-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5cd71-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5cd71-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cd71-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5cd71-109">Requirements</span></span>  
 <span data-ttu-id="5cd71-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cd71-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cd71-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5cd71-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5cd71-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5cd71-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5cd71-113">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cd71-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cd71-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5cd71-114">See also</span></span>

- [<span data-ttu-id="5cd71-115">ICorDebugLoadedModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5cd71-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="5cd71-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="5cd71-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
