---
title: "CorThreadSafetyOptions – výčet"
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
- CorThreadSafetyOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorThreadSafetyOptions
helpviewer_keywords:
- CorThreadSafetyOptions enumeration [.NET Framework metadata]
ms.assetid: dae07d9b-df51-488c-b17e-52d6e48217bd
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e017732882841e1cb2b5f00b1c51e22bba11ae73
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corthreadsafetyoptions-enumeration"></a><span data-ttu-id="a9111-102">CorThreadSafetyOptions – výčet</span><span class="sxs-lookup"><span data-stu-id="a9111-102">CorThreadSafetyOptions Enumeration</span></span>
<span data-ttu-id="a9111-103">Určuje příznaky výběr možností pro bezpečný přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="a9111-103">Specifies flags to select options for thread safety.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9111-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9111-104">Syntax</span></span>  
  
```  
typedef enum CorThreadSafetyOptions {  
    MDThreadSafetyDefault       = 0x00000000,  
    MDThreadSafetyOff           = 0x00000000,  
    MDThreadSafetyOn            = 0x00000001,  
} CorThreadSafetyOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="a9111-105">Členové</span><span class="sxs-lookup"><span data-stu-id="a9111-105">Members</span></span>  
  
|<span data-ttu-id="a9111-106">Člen</span><span class="sxs-lookup"><span data-stu-id="a9111-106">Member</span></span>|<span data-ttu-id="a9111-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a9111-107">Description</span></span>|  
|------------|-----------------|  
|`MDThreadSatetyDefault`|<span data-ttu-id="a9111-108">Výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="a9111-108">Default value.</span></span> <span data-ttu-id="a9111-109">Stejné jako `MDThreadSatetyOff`.</span><span class="sxs-lookup"><span data-stu-id="a9111-109">Same as `MDThreadSatetyOff`.</span></span>|  
|`MDThreadSatetyOff`|<span data-ttu-id="a9111-110">Označuje, že nelze nastavit zámek pro čtečky nebo zápis.</span><span class="sxs-lookup"><span data-stu-id="a9111-110">Indicates that a reader/writer lock cannot be set.</span></span>|  
|`MDThreadSatetyOn`|<span data-ttu-id="a9111-111">Označuje, zda lze nastavit zámek pro čtečky nebo zápis.</span><span class="sxs-lookup"><span data-stu-id="a9111-111">Indicates that a reader/writer lock can be set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a9111-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a9111-112">Requirements</span></span>  
 <span data-ttu-id="a9111-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9111-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9111-114">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="a9111-114">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="a9111-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9111-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9111-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="a9111-116">See Also</span></span>  
 [<span data-ttu-id="a9111-117">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="a9111-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
