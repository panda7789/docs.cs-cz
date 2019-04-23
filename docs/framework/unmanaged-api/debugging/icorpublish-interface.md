---
title: ICorPublish – rozhraní
ms.date: 03/30/2017
api_name:
- ICorPublish
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish
helpviewer_keywords:
- ICorPublish interface [.NET Framework debugging]
ms.assetid: 87c4fcb2-7703-4a2e-afb6-42973381b960
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7581d68f5c2b575403ddc84d06147f012e7ab39e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59076338"
---
# <a name="icorpublish-interface"></a><span data-ttu-id="827af-102">ICorPublish – rozhraní</span><span class="sxs-lookup"><span data-stu-id="827af-102">ICorPublish Interface</span></span>
<span data-ttu-id="827af-103">Slouží jako obecné rozhraní pro publikování informací o procesech a informace o doménách aplikace v těchto procesů.</span><span class="sxs-lookup"><span data-stu-id="827af-103">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="827af-104">Metody</span><span class="sxs-lookup"><span data-stu-id="827af-104">Methods</span></span>  
  
|<span data-ttu-id="827af-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="827af-105">Method</span></span>|<span data-ttu-id="827af-106">Popis</span><span class="sxs-lookup"><span data-stu-id="827af-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="827af-107">EnumProcesses – metoda</span><span class="sxs-lookup"><span data-stu-id="827af-107">EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md)|<span data-ttu-id="827af-108">Získá [icorpublishprocessenum –](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance, která obsahuje spravované procesy v tomto počítači spuštěna.</span><span class="sxs-lookup"><span data-stu-id="827af-108">Gets an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="827af-109">GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="827af-109">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-getprocess-method.md)|<span data-ttu-id="827af-110">Získá [icorpublishprocess –](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instanci, která představuje proces se zadaným identifikátorem.</span><span class="sxs-lookup"><span data-stu-id="827af-110">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="827af-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="827af-111">Requirements</span></span>  
 <span data-ttu-id="827af-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="827af-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="827af-113">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="827af-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="827af-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="827af-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="827af-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="827af-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="827af-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="827af-116">See also</span></span>

- [<span data-ttu-id="827af-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="827af-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="827af-118">CorpubPublish – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="827af-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
