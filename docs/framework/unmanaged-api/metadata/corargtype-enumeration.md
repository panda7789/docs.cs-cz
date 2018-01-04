---
title: "CorArgType – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorArgType
api_location: mscoree.dll
api_type: COM
f1_keywords: CorArgType
helpviewer_keywords: CorArgType enumeration [.NET Framework metadata]
ms.assetid: 3c1cb268-57a0-4664-91c7-f6908ff29e32
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dfc632849249c437769ce547b2b7facfd97333e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corargtype-enumeration"></a><span data-ttu-id="39871-102">CorArgType – výčet</span><span class="sxs-lookup"><span data-stu-id="39871-102">CorArgType Enumeration</span></span>
<span data-ttu-id="39871-103">Obsahuje hodnoty, které popisují nativní typ popisovače modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="39871-103">Contains values that describe the native type of a runtime handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39871-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39871-104">Syntax</span></span>  
  
```  
typedef enum CorArgType {  
  
    IMAGE_CEE_CS_END        = 0x0,  
    IMAGE_CEE_CS_VOID       = 0x1,  
    IMAGE_CEE_CS_I4         = 0x2,  
    IMAGE_CEE_CS_I8         = 0x3,  
    IMAGE_CEE_CS_R4         = 0x4,  
    IMAGE_CEE_CS_R8         = 0x5,  
    IMAGE_CEE_CS_PTR        = 0x6,  
    IMAGE_CEE_CS_OBJECT     = 0x7,  
    IMAGE_CEE_CS_STRUCT4    = 0x8,  
    IMAGE_CEE_CS_STRUCT32   = 0x9,  
    IMAGE_CEE_CS_BYVALUE    = 0xA  
  
} CorArgType;  
```  
  
## <a name="requirements"></a><span data-ttu-id="39871-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="39871-105">Requirements</span></span>  
 <span data-ttu-id="39871-106">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39871-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39871-107">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="39871-107">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="39871-108">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39871-108">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39871-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="39871-109">See Also</span></span>  
 [<span data-ttu-id="39871-110">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="39871-110">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
