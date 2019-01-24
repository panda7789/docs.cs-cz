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
ms.openlocfilehash: c1ee52e993859963984f7468e41a5daf3a77ba26
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54621666"
---
# <a name="icordebugmetadatalocator-interface"></a><span data-ttu-id="d1d69-102">ICorDebugMetaDataLocator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d1d69-102">ICorDebugMetaDataLocator Interface</span></span>
<span data-ttu-id="d1d69-103">Poskytuje informace metadat k ladicímu programu.</span><span class="sxs-lookup"><span data-stu-id="d1d69-103">Provides metadata information to the debugger.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d1d69-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d1d69-104">Methods</span></span>  
  
|<span data-ttu-id="d1d69-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d1d69-105">Method</span></span>|<span data-ttu-id="d1d69-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d1d69-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d1d69-107">GetMetaData – metoda</span><span class="sxs-lookup"><span data-stu-id="d1d69-107">GetMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-getmetadata-method.md)|<span data-ttu-id="d1d69-108">Dotaz vrátí úplnou cestu k modulu, jehož metadat je potřeba k dokončení operace, které ladicí program požadovaný ladicí program.</span><span class="sxs-lookup"><span data-stu-id="d1d69-108">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1d69-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d1d69-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1d69-110">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="d1d69-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1d69-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d1d69-111">Requirements</span></span>  
 <span data-ttu-id="d1d69-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1d69-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1d69-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d1d69-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1d69-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1d69-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1d69-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1d69-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1d69-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d1d69-116">See also</span></span>
- [<span data-ttu-id="d1d69-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="d1d69-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="d1d69-118">Ladění</span><span class="sxs-lookup"><span data-stu-id="d1d69-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
