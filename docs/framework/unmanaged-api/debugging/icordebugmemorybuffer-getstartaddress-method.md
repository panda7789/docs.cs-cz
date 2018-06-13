---
title: ICorDebugMemoryBuffer::GetStartAddress – metoda
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1aa816ea9e6185791e09bcdb0e47c50761a5ebc6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422930"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="9b24f-102">ICorDebugMemoryBuffer::GetStartAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="9b24f-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="9b24f-103">Získá počáteční adresa vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="9b24f-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b24f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b24f-104">Syntax</span></span>  
  
```  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9b24f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9b24f-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="9b24f-106">[out] Ukazatel na počáteční adresa vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="9b24f-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b24f-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9b24f-107">Remarks</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="9b24f-108">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="9b24f-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b24f-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9b24f-109">Requirements</span></span>  
 <span data-ttu-id="9b24f-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b24f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b24f-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b24f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b24f-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b24f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b24f-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b24f-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b24f-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="9b24f-114">See Also</span></span>  
 [<span data-ttu-id="9b24f-115">ICorDebugMemoryBuffer – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9b24f-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="9b24f-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="9b24f-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
