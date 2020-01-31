---
title: Metoda ICorDebugLoadedModule::GetSize
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
ms.openlocfilehash: f207cd1c612b6444a9512adaa356ac2d01de7b9f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788468"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="79c76-102">Metoda ICorDebugLoadedModule::GetSize</span><span class="sxs-lookup"><span data-stu-id="79c76-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="79c76-103">Získá velikost načteného modulu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="79c76-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79c76-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79c76-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79c76-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="79c76-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="79c76-106">mimo Ukazatel na počet bajtů v načteném modulu.</span><span class="sxs-lookup"><span data-stu-id="79c76-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79c76-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="79c76-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="79c76-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="79c76-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79c76-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="79c76-109">Requirements</span></span>  
 <span data-ttu-id="79c76-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79c76-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79c76-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="79c76-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79c76-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="79c76-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79c76-113">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79c76-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79c76-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="79c76-114">See also</span></span>

- [<span data-ttu-id="79c76-115">ICorDebugLoadedModule – rozhraní</span><span class="sxs-lookup"><span data-stu-id="79c76-115">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="79c76-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="79c76-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
