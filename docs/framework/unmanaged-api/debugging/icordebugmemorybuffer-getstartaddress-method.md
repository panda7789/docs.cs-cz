---
title: "ICorDebugMemoryBuffer::GetStartAddress – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5519b9dd0d85114e08311e1263c2f2e4ab095ae6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="8b6da-102">ICorDebugMemoryBuffer::GetStartAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="8b6da-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="8b6da-103">Získá počáteční adresa vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="8b6da-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b6da-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b6da-104">Syntax</span></span>  
  
```  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8b6da-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b6da-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="8b6da-106">[out] Ukazatel na počáteční adresa vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="8b6da-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b6da-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8b6da-107">Remarks</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="8b6da-108">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="8b6da-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b6da-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8b6da-109">Requirements</span></span>  
 <span data-ttu-id="8b6da-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b6da-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b6da-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b6da-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b6da-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b6da-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b6da-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b6da-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b6da-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="8b6da-114">See Also</span></span>  
 [<span data-ttu-id="8b6da-115">ICorDebugMemoryBuffer – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8b6da-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="8b6da-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="8b6da-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
