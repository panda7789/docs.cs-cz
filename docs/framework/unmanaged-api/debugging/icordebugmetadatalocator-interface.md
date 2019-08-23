---
title: ICorDebugMetaDataLocator – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugMetaDataLocator
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMetaDataLocator
helpviewer_keywords:
- ICorDebugMetaDataLocator interface [.NET Framework debugging]
ms.assetid: 287f5ecd-863f-4090-a615-077859f0257b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 64cf11ec294486fdc14d424e731eac8e4745d892
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939857"
---
# <a name="icordebugmetadatalocator-interface"></a><span data-ttu-id="41702-102">ICorDebugMetaDataLocator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="41702-102">ICorDebugMetaDataLocator Interface</span></span>
<span data-ttu-id="41702-103">Poskytuje informace metadat k ladicímu programu.</span><span class="sxs-lookup"><span data-stu-id="41702-103">Provides metadata information to the debugger.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="41702-104">Metody</span><span class="sxs-lookup"><span data-stu-id="41702-104">Methods</span></span>  
  
|<span data-ttu-id="41702-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="41702-105">Method</span></span>|<span data-ttu-id="41702-106">Popis</span><span class="sxs-lookup"><span data-stu-id="41702-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="41702-107">GetMetaData – metoda</span><span class="sxs-lookup"><span data-stu-id="41702-107">GetMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-getmetadata-method.md)|<span data-ttu-id="41702-108">Požádá ladicí program, aby vrátil úplnou cestu k modulu, jehož metadata jsou potřeba k dokončení operace, kterou ladicí program požaduje.</span><span class="sxs-lookup"><span data-stu-id="41702-108">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41702-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="41702-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="41702-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="41702-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41702-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="41702-111">Requirements</span></span>  
 <span data-ttu-id="41702-112">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41702-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41702-113">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="41702-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41702-114">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41702-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41702-115">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41702-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41702-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="41702-116">See also</span></span>

- [<span data-ttu-id="41702-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="41702-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="41702-118">Ladění</span><span class="sxs-lookup"><span data-stu-id="41702-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
