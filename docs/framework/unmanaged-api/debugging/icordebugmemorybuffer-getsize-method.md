---
title: ICorDebugMemoryBuffer::GetSize – metoda
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d687f2bbd3c20564368d4246961b56382ea14cf5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59099674"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="3b94d-102">ICorDebugMemoryBuffer::GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="3b94d-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="3b94d-103">Získá velikost vyrovnávací paměti v bajtech.</span><span class="sxs-lookup"><span data-stu-id="3b94d-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b94d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b94d-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b94d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3b94d-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="3b94d-106">[out] Ukazatel na velikost vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="3b94d-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b94d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3b94d-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b94d-108">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3b94d-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b94d-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3b94d-109">Requirements</span></span>  
 <span data-ttu-id="3b94d-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b94d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b94d-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3b94d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3b94d-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b94d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b94d-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b94d-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b94d-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3b94d-114">See also</span></span>

- [<span data-ttu-id="3b94d-115">ICorDebugMemoryBuffer – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3b94d-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="3b94d-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="3b94d-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
