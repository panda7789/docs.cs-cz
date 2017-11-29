---
title: "ICorDebugMergedAssemblyRecord::GetIndex – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dac64c785077fc3901e712498e66e11b9c9f3279
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a><span data-ttu-id="fbb4f-102">ICorDebugMergedAssemblyRecord::GetIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="fbb4f-102">ICorDebugMergedAssemblyRecord::GetIndex Method</span></span>
<span data-ttu-id="fbb4f-103">Získá index předpona je sestavení.</span><span class="sxs-lookup"><span data-stu-id="fbb4f-103">Gets the assembly's prefix index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbb4f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fbb4f-104">Syntax</span></span>  
  
```  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fbb4f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fbb4f-105">Parameters</span></span>  
 `pIndex`  
 <span data-ttu-id="fbb4f-106">[out] Ukazatel na index předponu.</span><span class="sxs-lookup"><span data-stu-id="fbb4f-106">[out] A pointer to the prefix index.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbb4f-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fbb4f-107">Remarks</span></span>  
 <span data-ttu-id="fbb4f-108">Index předpona se používá při prevenci kolize názvů v názvy typů sloučené metadat.</span><span class="sxs-lookup"><span data-stu-id="fbb4f-108">The prefix index is used to prevent name collisions in the merged metadata type names.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fbb4f-109">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="fbb4f-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbb4f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fbb4f-110">Requirements</span></span>  
 <span data-ttu-id="fbb4f-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbb4f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbb4f-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fbb4f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fbb4f-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fbb4f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fbb4f-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbb4f-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbb4f-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="fbb4f-115">See Also</span></span>  
 [<span data-ttu-id="fbb4f-116">ICorDebugMergedAssemblyRecord rozhraní</span><span class="sxs-lookup"><span data-stu-id="fbb4f-116">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="fbb4f-117">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="fbb4f-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
