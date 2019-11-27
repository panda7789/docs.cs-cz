---
title: CorArgType – výčet
ms.date: 03/30/2017
api_name:
- CorArgType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorArgType
helpviewer_keywords:
- CorArgType enumeration [.NET Framework metadata]
ms.assetid: 3c1cb268-57a0-4664-91c7-f6908ff29e32
topic_type:
- apiref
ms.openlocfilehash: 689295610006824be1107577c50376e79551cddc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444372"
---
# <a name="corargtype-enumeration"></a><span data-ttu-id="abbce-102">CorArgType – výčet</span><span class="sxs-lookup"><span data-stu-id="abbce-102">CorArgType Enumeration</span></span>
<span data-ttu-id="abbce-103">Obsahuje hodnoty, které popisují nativní typ popisovače modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="abbce-103">Contains values that describe the native type of a runtime handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abbce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="abbce-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="requirements"></a><span data-ttu-id="abbce-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="abbce-105">Requirements</span></span>  
 <span data-ttu-id="abbce-106">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abbce-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abbce-107">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="abbce-107">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="abbce-108">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abbce-108">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abbce-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="abbce-109">See also</span></span>

- [<span data-ttu-id="abbce-110">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="abbce-110">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
