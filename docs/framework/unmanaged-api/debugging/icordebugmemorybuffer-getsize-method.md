---
title: 'ICorDebugMemoryBuffer:: GetSize – metoda'
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c88d389f80b4b3d811d95f65acd41f294d076b3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969079"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="9a63c-102">ICorDebugMemoryBuffer:: GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="9a63c-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="9a63c-103">Získá velikost vyrovnávací paměti v bajtech.</span><span class="sxs-lookup"><span data-stu-id="9a63c-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a63c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a63c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a63c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9a63c-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="9a63c-106">mimo Ukazatel na velikost vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="9a63c-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a63c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9a63c-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9a63c-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9a63c-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a63c-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9a63c-109">Requirements</span></span>  
 <span data-ttu-id="9a63c-110">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a63c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a63c-111">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9a63c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a63c-112">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a63c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a63c-113">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a63c-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a63c-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9a63c-114">See also</span></span>

- [<span data-ttu-id="9a63c-115">ICorDebugMemoryBuffer – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a63c-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="9a63c-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="9a63c-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
