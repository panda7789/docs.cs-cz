---
title: 'ICorDebugMemoryBuffer:: GetSize – metoda'
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
ms.openlocfilehash: 1693860abe99884ee443be0666dfb6b485a219a0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127996"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="91040-102">ICorDebugMemoryBuffer:: GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="91040-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="91040-103">Získá velikost vyrovnávací paměti v bajtech.</span><span class="sxs-lookup"><span data-stu-id="91040-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91040-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91040-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91040-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="91040-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="91040-106">mimo Ukazatel na velikost vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="91040-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91040-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="91040-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="91040-108">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="91040-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91040-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="91040-109">Requirements</span></span>  
 <span data-ttu-id="91040-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91040-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91040-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="91040-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91040-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="91040-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91040-113">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91040-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91040-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91040-114">See also</span></span>

- [<span data-ttu-id="91040-115">ICorDebugMemoryBuffer – rozhraní</span><span class="sxs-lookup"><span data-stu-id="91040-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="91040-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="91040-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
