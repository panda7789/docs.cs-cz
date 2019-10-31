---
title: 'ICorDebugMemoryBuffer:: GetStartAddress – metoda'
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
ms.openlocfilehash: e2876398ceaf863bbb3c7e576d59b89c52f1bdaf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127991"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="ace68-102">ICorDebugMemoryBuffer:: GetStartAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="ace68-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="ace68-103">Získá počáteční adresu vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="ace68-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ace68-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ace68-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ace68-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ace68-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="ace68-106">mimo Ukazatel na počáteční adresu vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="ace68-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ace68-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ace68-107">Remarks</span></span>  
  
> [!WARNING]
> <span data-ttu-id="ace68-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ace68-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ace68-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ace68-109">Requirements</span></span>  
 <span data-ttu-id="ace68-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ace68-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ace68-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ace68-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ace68-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ace68-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ace68-113">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ace68-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ace68-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ace68-114">See also</span></span>

- [<span data-ttu-id="ace68-115">ICorDebugMemoryBuffer – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ace68-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="ace68-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="ace68-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
