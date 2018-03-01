---
title: "CeeSectionAttr – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CeeSectionAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionAttr
helpviewer_keywords:
- CeeSectionAttr enumeration [.NET Framework metadata]
ms.assetid: 0db51881-b869-4677-a715-1726a9216489
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 212d9be02a3c4ca97a6a69391ff82edb1d013d93
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ceesectionattr-enumeration"></a><span data-ttu-id="991a3-102">CeeSectionAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="991a3-102">CeeSectionAttr Enumeration</span></span>
<span data-ttu-id="991a3-103">Poskytuje hodnoty, které určit atributy oddílu pro použití [iceegen –](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="991a3-103">Provides values that specify attributes of a section for use by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="991a3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="991a3-104">Syntax</span></span>  
  
```  
typedef enum  {  
    sdNone      = 0,  
    sdReadOnly  = IMAGE_SCN_CNT_INITIALIZED_DATA |  
                  IMAGE_SCN_MEM_READ,  
    sdReadWrite = sdReadOnly | IMAGE_SCN_MEM_WRITE,  
    sdExecute   = IMAGE_SCN_MEM_READ | IMAGE_SCN_CNT_CODE |  
                  IMAGE_SCN_MEM_EXECUTE  
} CeeSectionAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="991a3-105">Členové</span><span class="sxs-lookup"><span data-stu-id="991a3-105">Members</span></span>  
  
|<span data-ttu-id="991a3-106">Člen</span><span class="sxs-lookup"><span data-stu-id="991a3-106">Member</span></span>|<span data-ttu-id="991a3-107">Popis</span><span class="sxs-lookup"><span data-stu-id="991a3-107">Description</span></span>|  
|------------|-----------------|  
|`sdNone`|<span data-ttu-id="991a3-108">Oddíl nemá žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="991a3-108">Section has no attributes.</span></span>|  
|`sdReadOnly`|<span data-ttu-id="991a3-109">Oddíl obsahuje inicializovaného data, která může být pouze číst, neaktualizuje.</span><span class="sxs-lookup"><span data-stu-id="991a3-109">Section contains initialized data that can be only read, not updated.</span></span>|  
|`sdReadWrite`|<span data-ttu-id="991a3-110">Oddíl obsahuje inicializovaného data, která můžou číst nebo aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="991a3-110">Section contains initialized data that can be read or updated.</span></span>|  
|`sdExecute`|<span data-ttu-id="991a3-111">Oddíl obsahuje spustitelného kódu, který může číst a spustit.</span><span class="sxs-lookup"><span data-stu-id="991a3-111">Section contains executable code that is allowed to be read and executed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="991a3-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="991a3-112">Requirements</span></span>  
 <span data-ttu-id="991a3-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="991a3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="991a3-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="991a3-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="991a3-115">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="991a3-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="991a3-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="991a3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="991a3-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="991a3-117">See Also</span></span>  
 [<span data-ttu-id="991a3-118">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="991a3-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
