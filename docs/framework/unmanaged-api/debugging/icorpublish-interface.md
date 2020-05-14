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
ms.openlocfilehash: 1bd2f537cfa6a27c24ba91ea7caa29dc9e71a74e
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396324"
---
# <a name="icorpublish-interface"></a><span data-ttu-id="815f2-102">ICorPublish – rozhraní</span><span class="sxs-lookup"><span data-stu-id="815f2-102">ICorPublish Interface</span></span>
<span data-ttu-id="815f2-103">Slouží jako obecné rozhraní pro publikování informací o procesech a informacích o doménách aplikace v těchto procesech.</span><span class="sxs-lookup"><span data-stu-id="815f2-103">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="815f2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="815f2-104">Methods</span></span>  
  
|<span data-ttu-id="815f2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="815f2-105">Method</span></span>|<span data-ttu-id="815f2-106">Popis</span><span class="sxs-lookup"><span data-stu-id="815f2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="815f2-107">EnumProcesses – metoda</span><span class="sxs-lookup"><span data-stu-id="815f2-107">EnumProcesses Method</span></span>](icorpublish-enumprocesses-method.md)|<span data-ttu-id="815f2-108">Získá instanci [ICorPublishProcessEnum –](icorpublishprocessenum-interface.md) , která obsahuje spravované procesy spuštěné v tomto počítači.</span><span class="sxs-lookup"><span data-stu-id="815f2-108">Gets an [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="815f2-109">GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="815f2-109">GetProcess Method</span></span>](icorpublish-getprocess-method.md)|<span data-ttu-id="815f2-110">Získá instanci [ICorPublishProcess](icorpublishprocess-interface.md) , která představuje proces se zadaným identifikátorem.</span><span class="sxs-lookup"><span data-stu-id="815f2-110">Gets an [ICorPublishProcess](icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="815f2-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="815f2-111">Requirements</span></span>  
 <span data-ttu-id="815f2-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="815f2-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="815f2-113">**Hlavička:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="815f2-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="815f2-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="815f2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="815f2-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="815f2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="815f2-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="815f2-116">See also</span></span>

- [<span data-ttu-id="815f2-117">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="815f2-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="815f2-118">CorpubPublish – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="815f2-118">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
