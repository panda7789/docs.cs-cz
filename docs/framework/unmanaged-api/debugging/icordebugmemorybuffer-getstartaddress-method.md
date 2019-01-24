---
title: ICorDebugMemoryBuffer::GetStartAddress – metoda
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 29149ceb155cdfdf7b735d6939809e80f2ba4dc0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54695540"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="8aa87-102">ICorDebugMemoryBuffer::GetStartAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="8aa87-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="8aa87-103">Získá počáteční adresa vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="8aa87-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8aa87-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8aa87-104">Syntax</span></span>  
  
```  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8aa87-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8aa87-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="8aa87-106">[out] Ukazatel na počáteční adresa vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="8aa87-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8aa87-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8aa87-107">Remarks</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="8aa87-108">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8aa87-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8aa87-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8aa87-109">Requirements</span></span>  
 <span data-ttu-id="8aa87-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8aa87-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8aa87-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8aa87-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8aa87-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8aa87-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8aa87-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8aa87-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aa87-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8aa87-114">See also</span></span>
- [<span data-ttu-id="8aa87-115">ICorDebugMemoryBuffer – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8aa87-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="8aa87-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="8aa87-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
