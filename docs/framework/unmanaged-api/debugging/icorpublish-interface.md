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
ms.openlocfilehash: 70cf2d76c7c5d1c3431506685f8506e44ab9ec4a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121771"
---
# <a name="icorpublish-interface"></a><span data-ttu-id="7e854-102">ICorPublish – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7e854-102">ICorPublish Interface</span></span>
<span data-ttu-id="7e854-103">Slouží jako obecné rozhraní pro publikování informací o procesech a informacích o doménách aplikace v těchto procesech.</span><span class="sxs-lookup"><span data-stu-id="7e854-103">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7e854-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7e854-104">Methods</span></span>  
  
|<span data-ttu-id="7e854-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7e854-105">Method</span></span>|<span data-ttu-id="7e854-106">Popis</span><span class="sxs-lookup"><span data-stu-id="7e854-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7e854-107">EnumProcesses – metoda</span><span class="sxs-lookup"><span data-stu-id="7e854-107">EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md)|<span data-ttu-id="7e854-108">Získá instanci [ICorPublishProcessEnum –](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) , která obsahuje spravované procesy spuštěné v tomto počítači.</span><span class="sxs-lookup"><span data-stu-id="7e854-108">Gets an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="7e854-109">GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="7e854-109">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-getprocess-method.md)|<span data-ttu-id="7e854-110">Získá instanci [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) , která představuje proces se zadaným identifikátorem.</span><span class="sxs-lookup"><span data-stu-id="7e854-110">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7e854-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7e854-111">Requirements</span></span>  
 <span data-ttu-id="7e854-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e854-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e854-113">**Hlavička:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="7e854-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="7e854-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7e854-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e854-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e854-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e854-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7e854-116">See also</span></span>

- [<span data-ttu-id="7e854-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="7e854-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="7e854-118">CorpubPublish – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="7e854-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
