---
title: CorThreadSafetyOptions – výčet
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b460c2c4b0d38ec46ee9d7341de9b320a2ecaa7e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54594639"
---
# <a name="corthreadsafetyoptions-enumeration"></a><span data-ttu-id="3b5b3-102">CorThreadSafetyOptions – výčet</span><span class="sxs-lookup"><span data-stu-id="3b5b3-102">CorThreadSafetyOptions Enumeration</span></span>
<span data-ttu-id="3b5b3-103">Určuje příznaky a možnosti pro bezpečný přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="3b5b3-103">Specifies flags to select options for thread safety.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b5b3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b5b3-104">Syntax</span></span>  
  
```  
typedef enum CorThreadSafetyOptions {  
    MDThreadSafetyDefault       = 0x00000000,  
    MDThreadSafetyOff           = 0x00000000,  
    MDThreadSafetyOn            = 0x00000001,  
} CorThreadSafetyOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="3b5b3-105">Členové</span><span class="sxs-lookup"><span data-stu-id="3b5b3-105">Members</span></span>  
  
|<span data-ttu-id="3b5b3-106">Člen</span><span class="sxs-lookup"><span data-stu-id="3b5b3-106">Member</span></span>|<span data-ttu-id="3b5b3-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3b5b3-107">Description</span></span>|  
|------------|-----------------|  
|`MDThreadSatetyDefault`|<span data-ttu-id="3b5b3-108">Výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="3b5b3-108">Default value.</span></span> <span data-ttu-id="3b5b3-109">Stejné jako `MDThreadSatetyOff`.</span><span class="sxs-lookup"><span data-stu-id="3b5b3-109">Same as `MDThreadSatetyOff`.</span></span>|  
|`MDThreadSatetyOff`|<span data-ttu-id="3b5b3-110">Označuje, že zámek čtení/zápis nelze nastavit.</span><span class="sxs-lookup"><span data-stu-id="3b5b3-110">Indicates that a reader/writer lock cannot be set.</span></span>|  
|`MDThreadSatetyOn`|<span data-ttu-id="3b5b3-111">Označuje, že můžete nastavit zámek čtení/zápis.</span><span class="sxs-lookup"><span data-stu-id="3b5b3-111">Indicates that a reader/writer lock can be set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3b5b3-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3b5b3-112">Requirements</span></span>  
 <span data-ttu-id="3b5b3-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b5b3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b5b3-114">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="3b5b3-114">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="3b5b3-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b5b3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b5b3-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3b5b3-116">See also</span></span>
- [<span data-ttu-id="3b5b3-117">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="3b5b3-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
