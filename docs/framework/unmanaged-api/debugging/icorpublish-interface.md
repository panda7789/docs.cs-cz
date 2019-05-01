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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993570"
---
# <a name="icorpublish-interface"></a><span data-ttu-id="3e78d-102">ICorPublish – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3e78d-102">ICorPublish Interface</span></span>
<span data-ttu-id="3e78d-103">Slouží jako obecné rozhraní pro publikování informací o procesech a informace o doménách aplikace v těchto procesů.</span><span class="sxs-lookup"><span data-stu-id="3e78d-103">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3e78d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3e78d-104">Methods</span></span>  
  
|<span data-ttu-id="3e78d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3e78d-105">Method</span></span>|<span data-ttu-id="3e78d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="3e78d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3e78d-107">EnumProcesses – metoda</span><span class="sxs-lookup"><span data-stu-id="3e78d-107">EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md)|<span data-ttu-id="3e78d-108">Získá [icorpublishprocessenum –](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance, která obsahuje spravované procesy v tomto počítači spuštěna.</span><span class="sxs-lookup"><span data-stu-id="3e78d-108">Gets an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="3e78d-109">GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="3e78d-109">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-getprocess-method.md)|<span data-ttu-id="3e78d-110">Získá [icorpublishprocess –](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instanci, která představuje proces se zadaným identifikátorem.</span><span class="sxs-lookup"><span data-stu-id="3e78d-110">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3e78d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3e78d-111">Requirements</span></span>  
 <span data-ttu-id="3e78d-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e78d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e78d-113">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="3e78d-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="3e78d-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e78d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e78d-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e78d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e78d-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3e78d-116">See also</span></span>

- [<span data-ttu-id="3e78d-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="3e78d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="3e78d-118">CorpubPublish – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="3e78d-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
