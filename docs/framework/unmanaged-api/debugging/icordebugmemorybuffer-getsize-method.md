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
ms.openlocfilehash: a21198c70512af703e106870d1bc3f7882d62fe9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="eb6fb-102">ICorDebugMemoryBuffer::GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="eb6fb-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="eb6fb-103">Získá velikost vyrovnávací paměti v bajtech.</span><span class="sxs-lookup"><span data-stu-id="eb6fb-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb6fb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb6fb-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eb6fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eb6fb-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="eb6fb-106">[out] Ukazatel na velikost vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="eb6fb-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb6fb-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eb6fb-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eb6fb-108">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="eb6fb-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb6fb-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eb6fb-109">Requirements</span></span>  
 <span data-ttu-id="eb6fb-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb6fb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb6fb-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eb6fb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eb6fb-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb6fb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb6fb-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb6fb-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb6fb-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb6fb-114">See Also</span></span>  
 [<span data-ttu-id="eb6fb-115">ICorDebugMemoryBuffer rozhraní</span><span class="sxs-lookup"><span data-stu-id="eb6fb-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="eb6fb-116">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="eb6fb-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
