---
title: CorFileFlags – výčet
ms.date: 03/30/2017
api_name:
- CorFileFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileFlags
helpviewer_keywords:
- CorFileFlags enumeration [.NET Framework metadata]
ms.assetid: d16703fd-518f-412e-92cb-74433d11032e
topic_type:
- apiref
ms.openlocfilehash: c8c2757e99b80204ad52e69a596d62c55c369965
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007413"
---
# <a name="corfileflags-enumeration"></a><span data-ttu-id="67d67-102">CorFileFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="67d67-102">CorFileFlags Enumeration</span></span>
<span data-ttu-id="67d67-103">Obsahuje hodnoty, které popisují typ souboru definovaného voláním [IMetaDataAssemblyEmit::D efinefile](imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="67d67-103">Contains values that describe the type of file defined in a call to [IMetaDataAssemblyEmit::DefineFile](imetadataassemblyemit-definefile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67d67-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67d67-104">Syntax</span></span>  
  
```cpp  
typedef enum CorFileFlags {  
  
    ffContainsMetaData      =   0x0000,  
    ffContainsNoMetaData    =   0x0001  
  
} CorFileFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="67d67-105">Členové</span><span class="sxs-lookup"><span data-stu-id="67d67-105">Members</span></span>  
  
|<span data-ttu-id="67d67-106">Člen</span><span class="sxs-lookup"><span data-stu-id="67d67-106">Member</span></span>|<span data-ttu-id="67d67-107">Description</span><span class="sxs-lookup"><span data-stu-id="67d67-107">Description</span></span>|  
|------------|-----------------|  
|`ffContainsMetaData`|<span data-ttu-id="67d67-108">Označuje, že soubor není soubor prostředků.</span><span class="sxs-lookup"><span data-stu-id="67d67-108">Indicates that the file is not a resource file.</span></span>|  
|`ffContainsNoMetaData`|<span data-ttu-id="67d67-109">Označuje, že soubor, pravděpodobně soubor prostředků, neobsahuje metadata.</span><span class="sxs-lookup"><span data-stu-id="67d67-109">Indicates that the file, possibly a resource file, does not contain metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="67d67-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="67d67-110">Requirements</span></span>  
 <span data-ttu-id="67d67-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67d67-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67d67-112">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="67d67-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="67d67-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67d67-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67d67-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="67d67-114">See also</span></span>

- [<span data-ttu-id="67d67-115">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="67d67-115">Metadata Enumerations</span></span>](metadata-enumerations.md)
