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
ms.openlocfilehash: ac822dda30d697cbbbcacf19eb6a57d1e5fb4c3b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007946"
---
# <a name="corargtype-enumeration"></a><span data-ttu-id="eb705-102">CorArgType – výčet</span><span class="sxs-lookup"><span data-stu-id="eb705-102">CorArgType Enumeration</span></span>
<span data-ttu-id="eb705-103">Obsahuje hodnoty, které popisují nativní typ popisovače modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="eb705-103">Contains values that describe the native type of a runtime handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb705-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb705-104">Syntax</span></span>  
  
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
  
## <a name="requirements"></a><span data-ttu-id="eb705-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eb705-105">Requirements</span></span>  
 <span data-ttu-id="eb705-106">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb705-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb705-107">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="eb705-107">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="eb705-108">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb705-108">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb705-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb705-109">See also</span></span>

- [<span data-ttu-id="eb705-110">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="eb705-110">Metadata Enumerations</span></span>](metadata-enumerations.md)
