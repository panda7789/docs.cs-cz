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
ms.openlocfilehash: c4a24d879ebd9e8813ea0ac4597818569f4ae6fa
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790729"
---
# <a name="icorpublish-interface"></a><span data-ttu-id="632df-102">ICorPublish – rozhraní</span><span class="sxs-lookup"><span data-stu-id="632df-102">ICorPublish Interface</span></span>
<span data-ttu-id="632df-103">Slouží jako obecné rozhraní pro publikování informací o procesech a informacích o doménách aplikace v těchto procesech.</span><span class="sxs-lookup"><span data-stu-id="632df-103">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="632df-104">Metody</span><span class="sxs-lookup"><span data-stu-id="632df-104">Methods</span></span>  
  
|<span data-ttu-id="632df-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="632df-105">Method</span></span>|<span data-ttu-id="632df-106">Popis</span><span class="sxs-lookup"><span data-stu-id="632df-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="632df-107">EnumProcesses – metoda</span><span class="sxs-lookup"><span data-stu-id="632df-107">EnumProcesses Method</span></span>](icorpublish-enumprocesses-method.md)|<span data-ttu-id="632df-108">Získá instanci [ICorPublishProcessEnum –](icorpublishprocessenum-interface.md) , která obsahuje spravované procesy spuštěné v tomto počítači.</span><span class="sxs-lookup"><span data-stu-id="632df-108">Gets an [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="632df-109">GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="632df-109">GetProcess Method</span></span>](icorpublish-getprocess-method.md)|<span data-ttu-id="632df-110">Získá instanci [ICorPublishProcess](icorpublishprocess-interface.md) , která představuje proces se zadaným identifikátorem.</span><span class="sxs-lookup"><span data-stu-id="632df-110">Gets an [ICorPublishProcess](icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="632df-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="632df-111">Requirements</span></span>  
 <span data-ttu-id="632df-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="632df-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="632df-113">**Hlavička:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="632df-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="632df-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="632df-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="632df-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="632df-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="632df-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="632df-116">See also</span></span>

- [<span data-ttu-id="632df-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="632df-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="632df-118">CorpubPublish – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="632df-118">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
