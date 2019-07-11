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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5c6ac7dabd2dfcc7829fd42389c0a6c261fe456d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781871"
---
# <a name="corfileflags-enumeration"></a><span data-ttu-id="a1871-102">CorFileFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="a1871-102">CorFileFlags Enumeration</span></span>
<span data-ttu-id="a1871-103">Obsahuje hodnoty, které popisují typ souboru definovaného parametrem volání [imetadataassemblyemit::definefile –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="a1871-103">Contains values that describe the type of file defined in a call to [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1871-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1871-104">Syntax</span></span>  
  
```cpp  
typedef enum CorFileFlags {  
  
    ffContainsMetaData      =   0x0000,  
    ffContainsNoMetaData    =   0x0001  
  
} CorFileFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="a1871-105">Členové</span><span class="sxs-lookup"><span data-stu-id="a1871-105">Members</span></span>  
  
|<span data-ttu-id="a1871-106">Člen</span><span class="sxs-lookup"><span data-stu-id="a1871-106">Member</span></span>|<span data-ttu-id="a1871-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a1871-107">Description</span></span>|  
|------------|-----------------|  
|`ffContainsMetaData`|<span data-ttu-id="a1871-108">Označuje, že soubor není soubor prostředků.</span><span class="sxs-lookup"><span data-stu-id="a1871-108">Indicates that the file is not a resource file.</span></span>|  
|`ffContainsNoMetaData`|<span data-ttu-id="a1871-109">Označuje, že soubor, případně souboru prostředků, neobsahuje metadata.</span><span class="sxs-lookup"><span data-stu-id="a1871-109">Indicates that the file, possibly a resource file, does not contain metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a1871-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a1871-110">Requirements</span></span>  
 <span data-ttu-id="a1871-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1871-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1871-112">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="a1871-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="a1871-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1871-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1871-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a1871-114">See also</span></span>

- [<span data-ttu-id="a1871-115">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="a1871-115">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
