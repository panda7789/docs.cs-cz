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
ms.openlocfilehash: 4e9b9221aa2f5e048a94c225660ba2ac9214549c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108824"
---
# <a name="icordebugmetadatalocator-interface"></a><span data-ttu-id="bdf65-102">ICorDebugMetaDataLocator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bdf65-102">ICorDebugMetaDataLocator Interface</span></span>
<span data-ttu-id="bdf65-103">Poskytuje informace metadat k ladicímu programu.</span><span class="sxs-lookup"><span data-stu-id="bdf65-103">Provides metadata information to the debugger.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bdf65-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bdf65-104">Methods</span></span>  
  
|<span data-ttu-id="bdf65-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bdf65-105">Method</span></span>|<span data-ttu-id="bdf65-106">Popis</span><span class="sxs-lookup"><span data-stu-id="bdf65-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bdf65-107">GetMetaData – metoda</span><span class="sxs-lookup"><span data-stu-id="bdf65-107">GetMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-getmetadata-method.md)|<span data-ttu-id="bdf65-108">Dotaz vrátí úplnou cestu k modulu, jehož metadat je potřeba k dokončení operace, které ladicí program požadovaný ladicí program.</span><span class="sxs-lookup"><span data-stu-id="bdf65-108">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bdf65-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bdf65-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bdf65-110">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="bdf65-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdf65-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bdf65-111">Requirements</span></span>  
 <span data-ttu-id="bdf65-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdf65-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdf65-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bdf65-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bdf65-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bdf65-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="bdf65-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="bdf65-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bdf65-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bdf65-116">See also</span></span>

- [<span data-ttu-id="bdf65-117">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bdf65-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="bdf65-118">Ladění</span><span class="sxs-lookup"><span data-stu-id="bdf65-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
