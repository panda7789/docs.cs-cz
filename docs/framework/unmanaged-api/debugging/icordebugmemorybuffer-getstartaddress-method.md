---
title: ICorDebugMemoryBuffer::GetStartAddress – metoda
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58649a0fc12ce63a1307af5d831dbf5e0d5a776a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136978"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="73de0-102">ICorDebugMemoryBuffer::GetStartAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="73de0-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="73de0-103">Získá počáteční adresa vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="73de0-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73de0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73de0-104">Syntax</span></span>  
  
```  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73de0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="73de0-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="73de0-106">[out] Ukazatel na počáteční adresa vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="73de0-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73de0-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="73de0-107">Remarks</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="73de0-108">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="73de0-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73de0-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="73de0-109">Requirements</span></span>  
 <span data-ttu-id="73de0-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73de0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73de0-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73de0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73de0-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73de0-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="73de0-113">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="73de0-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="73de0-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="73de0-114">See also</span></span>

- [<span data-ttu-id="73de0-115">ICorDebugMemoryBuffer – rozhraní</span><span class="sxs-lookup"><span data-stu-id="73de0-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="73de0-116">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="73de0-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
