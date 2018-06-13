---
title: ICorDebugMergedAssemblyRecord::GetIndex – metoda
ms.date: 03/30/2017
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0bcb5cdb4e93ae8ce6981bd86f125ecccb7d732
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414828"
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a><span data-ttu-id="33e73-102">ICorDebugMergedAssemblyRecord::GetIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="33e73-102">ICorDebugMergedAssemblyRecord::GetIndex Method</span></span>
<span data-ttu-id="33e73-103">Získá index předpona je sestavení.</span><span class="sxs-lookup"><span data-stu-id="33e73-103">Gets the assembly's prefix index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33e73-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33e73-104">Syntax</span></span>  
  
```  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="33e73-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="33e73-105">Parameters</span></span>  
 `pIndex`  
 <span data-ttu-id="33e73-106">[out] Ukazatel na index předponu.</span><span class="sxs-lookup"><span data-stu-id="33e73-106">[out] A pointer to the prefix index.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33e73-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="33e73-107">Remarks</span></span>  
 <span data-ttu-id="33e73-108">Index předpona se používá při prevenci kolize názvů v názvy typů sloučené metadat.</span><span class="sxs-lookup"><span data-stu-id="33e73-108">The prefix index is used to prevent name collisions in the merged metadata type names.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33e73-109">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="33e73-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33e73-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="33e73-110">Requirements</span></span>  
 <span data-ttu-id="33e73-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33e73-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33e73-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="33e73-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33e73-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33e73-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33e73-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33e73-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33e73-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="33e73-115">See Also</span></span>  
 [<span data-ttu-id="33e73-116">ICorDebugMergedAssemblyRecord – rozhraní</span><span class="sxs-lookup"><span data-stu-id="33e73-116">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="33e73-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="33e73-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
