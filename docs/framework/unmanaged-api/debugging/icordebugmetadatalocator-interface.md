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
ms.openlocfilehash: d1673b6045a6344ee0eeadf4ec3003206f92cde4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415675"
---
# <a name="icordebugmetadatalocator-interface"></a><span data-ttu-id="63cfe-102">ICorDebugMetaDataLocator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="63cfe-102">ICorDebugMetaDataLocator Interface</span></span>
<span data-ttu-id="63cfe-103">Poskytuje informace metadat k ladicímu programu.</span><span class="sxs-lookup"><span data-stu-id="63cfe-103">Provides metadata information to the debugger.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="63cfe-104">Metody</span><span class="sxs-lookup"><span data-stu-id="63cfe-104">Methods</span></span>  
  
|<span data-ttu-id="63cfe-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="63cfe-105">Method</span></span>|<span data-ttu-id="63cfe-106">Popis</span><span class="sxs-lookup"><span data-stu-id="63cfe-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="63cfe-107">GetMetaData – metoda</span><span class="sxs-lookup"><span data-stu-id="63cfe-107">GetMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-getmetadata-method.md)|<span data-ttu-id="63cfe-108">Požádá ladicí program na vrátit úplnou cestu k modulu, jehož metadat je potřebný pro dokončení operace, které požadovali ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="63cfe-108">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63cfe-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="63cfe-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63cfe-110">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="63cfe-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63cfe-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="63cfe-111">Requirements</span></span>  
 <span data-ttu-id="63cfe-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63cfe-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63cfe-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="63cfe-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63cfe-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63cfe-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63cfe-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63cfe-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63cfe-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="63cfe-116">See Also</span></span>  
 [<span data-ttu-id="63cfe-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="63cfe-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="63cfe-118">Ladění</span><span class="sxs-lookup"><span data-stu-id="63cfe-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
