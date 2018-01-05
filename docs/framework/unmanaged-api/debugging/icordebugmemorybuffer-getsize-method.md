---
title: "ICorDebugMemoryBuffer::GetSize – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 658fb2ce289b4b8cabfcf0cc2ea5f8dace2ec754
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="4bb86-102">ICorDebugMemoryBuffer::GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="4bb86-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="4bb86-103">Získá velikost vyrovnávací paměti v bajtech.</span><span class="sxs-lookup"><span data-stu-id="4bb86-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bb86-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4bb86-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4bb86-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4bb86-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="4bb86-106">[out] Ukazatel na velikost vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4bb86-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4bb86-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4bb86-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4bb86-108">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="4bb86-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bb86-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4bb86-109">Requirements</span></span>  
 <span data-ttu-id="4bb86-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bb86-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bb86-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4bb86-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4bb86-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4bb86-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4bb86-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bb86-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bb86-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="4bb86-114">See Also</span></span>  
 [<span data-ttu-id="4bb86-115">ICorDebugMemoryBuffer – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4bb86-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="4bb86-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="4bb86-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
