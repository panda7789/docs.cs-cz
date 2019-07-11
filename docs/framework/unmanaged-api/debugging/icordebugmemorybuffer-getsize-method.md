---
title: ICorDebugMemoryBuffer::GetSize – metoda
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0db104dbfa61b836aa01b99be45725ed4c04c798
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752791"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="6f51c-102">ICorDebugMemoryBuffer::GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="6f51c-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="6f51c-103">Získá velikost vyrovnávací paměti v bajtech.</span><span class="sxs-lookup"><span data-stu-id="6f51c-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f51c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f51c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f51c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6f51c-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="6f51c-106">[out] Ukazatel na velikost vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="6f51c-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f51c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6f51c-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f51c-108">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6f51c-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f51c-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6f51c-109">Requirements</span></span>  
 <span data-ttu-id="6f51c-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f51c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f51c-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6f51c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6f51c-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f51c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f51c-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f51c-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f51c-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6f51c-114">See also</span></span>

- [<span data-ttu-id="6f51c-115">ICorDebugMemoryBuffer – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6f51c-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="6f51c-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="6f51c-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
