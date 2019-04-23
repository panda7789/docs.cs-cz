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
ms.openlocfilehash: 076d5de3e9d1925e3a030fee4a06a89862105897
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59159611"
---
# <a name="corfileflags-enumeration"></a><span data-ttu-id="fa63a-102">CorFileFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="fa63a-102">CorFileFlags Enumeration</span></span>
<span data-ttu-id="fa63a-103">Obsahuje hodnoty, které popisují typ souboru definovaného parametrem volání [imetadataassemblyemit::definefile –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="fa63a-103">Contains values that describe the type of file defined in a call to [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa63a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fa63a-104">Syntax</span></span>  
  
```  
typedef enum CorFileFlags {  
  
    ffContainsMetaData      =   0x0000,  
    ffContainsNoMetaData    =   0x0001  
  
} CorFileFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="fa63a-105">Členové</span><span class="sxs-lookup"><span data-stu-id="fa63a-105">Members</span></span>  
  
|<span data-ttu-id="fa63a-106">Člen</span><span class="sxs-lookup"><span data-stu-id="fa63a-106">Member</span></span>|<span data-ttu-id="fa63a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="fa63a-107">Description</span></span>|  
|------------|-----------------|  
|`ffContainsMetaData`|<span data-ttu-id="fa63a-108">Označuje, že soubor není soubor prostředků.</span><span class="sxs-lookup"><span data-stu-id="fa63a-108">Indicates that the file is not a resource file.</span></span>|  
|`ffContainsNoMetaData`|<span data-ttu-id="fa63a-109">Označuje, že soubor, případně souboru prostředků, neobsahuje metadata.</span><span class="sxs-lookup"><span data-stu-id="fa63a-109">Indicates that the file, possibly a resource file, does not contain metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fa63a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fa63a-110">Requirements</span></span>  
 <span data-ttu-id="fa63a-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa63a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa63a-112">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="fa63a-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="fa63a-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa63a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa63a-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fa63a-114">See also</span></span>

- [<span data-ttu-id="fa63a-115">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="fa63a-115">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
