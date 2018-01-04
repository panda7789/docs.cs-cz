---
title: "ICorDebugSymbolProvider::GetAssemblyImageMetadata – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ff6b26dd9a0ed56e5194dc997270cf9d2dbe42b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="9c812-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata – metoda</span><span class="sxs-lookup"><span data-stu-id="9c812-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>
<span data-ttu-id="9c812-103">Vrátí metadata z sloučené sestavení.</span><span class="sxs-lookup"><span data-stu-id="9c812-103">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c812-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c812-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9c812-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9c812-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="9c812-106">[out] Ukazatel na adresu [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) objekt, který obsahuje informace o velikosti a adresu metadata sloučené sestavení.</span><span class="sxs-lookup"><span data-stu-id="9c812-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c812-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9c812-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9c812-108">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="9c812-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c812-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9c812-109">Requirements</span></span>  
 <span data-ttu-id="9c812-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c812-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c812-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9c812-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9c812-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c812-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c812-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c812-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c812-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="9c812-114">See Also</span></span>  
 [<span data-ttu-id="9c812-115">ICorDebugSymbolProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9c812-115">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="9c812-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="9c812-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
