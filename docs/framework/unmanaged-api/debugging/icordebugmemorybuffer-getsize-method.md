---
title: 'ICorDebugMemoryBuffer:: GetSize – metoda'
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
ms.openlocfilehash: 51c13b67951c714d1aec602ffea22891328565a0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793177"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="e06de-102">ICorDebugMemoryBuffer:: GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="e06de-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="e06de-103">Získá velikost vyrovnávací paměti v bajtech.</span><span class="sxs-lookup"><span data-stu-id="e06de-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e06de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e06de-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e06de-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e06de-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="e06de-106">mimo Ukazatel na velikost vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="e06de-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e06de-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e06de-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e06de-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e06de-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e06de-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e06de-109">Requirements</span></span>  
 <span data-ttu-id="e06de-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e06de-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e06de-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e06de-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e06de-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e06de-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e06de-113">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e06de-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e06de-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e06de-114">See also</span></span>

- [<span data-ttu-id="e06de-115">ICorDebugMemoryBuffer – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e06de-115">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="e06de-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e06de-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
