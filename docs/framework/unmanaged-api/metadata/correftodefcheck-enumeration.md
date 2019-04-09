---
title: CorRefToDefCheck – výčet
ms.date: 03/30/2017
api_name:
- CorRefToDefCheck
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRefToDefCheck
helpviewer_keywords:
- CorRefToDefCheck enumeration [.NET Framework metadata]
ms.assetid: f9a80f1a-55af-4459-b095-8441aae16119
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82abeb0ce3db075d794787bb1fcd5bc18321bef2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093888"
---
# <a name="correftodefcheck-enumeration"></a><span data-ttu-id="e66ad-102">CorRefToDefCheck – výčet</span><span class="sxs-lookup"><span data-stu-id="e66ad-102">CorRefToDefCheck Enumeration</span></span>
<span data-ttu-id="e66ad-103">Určuje příznaky do ovládacího prvku odkazované položky, které jsou převedeny na jejich definice, aby bylo možné optimalizovat kód.</span><span class="sxs-lookup"><span data-stu-id="e66ad-103">Specifies flags to control which referenced items are converted to their definitions in order to optimize the code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e66ad-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e66ad-104">Syntax</span></span>  
  
```  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a><span data-ttu-id="e66ad-105">Členové</span><span class="sxs-lookup"><span data-stu-id="e66ad-105">Members</span></span>  
  
|<span data-ttu-id="e66ad-106">Člen</span><span class="sxs-lookup"><span data-stu-id="e66ad-106">Member</span></span>|<span data-ttu-id="e66ad-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e66ad-107">Description</span></span>|  
|------------|-----------------|  
|`MDRefToDefDefault`|<span data-ttu-id="e66ad-108">Určuje typ odkazy a odkazy na členy mají být převedeny do definic.</span><span class="sxs-lookup"><span data-stu-id="e66ad-108">Specifies that type references and member references should be converted to definitions.</span></span> <span data-ttu-id="e66ad-109">Toto je výchozí hodnota (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span><span class="sxs-lookup"><span data-stu-id="e66ad-109">This is the default value (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span></span>|  
|`MDRefToDefAll`|<span data-ttu-id="e66ad-110">Určuje, zda všechny odkazované položky mají být převedeny na definice.</span><span class="sxs-lookup"><span data-stu-id="e66ad-110">Specifies that all referenced items should be converted to definitions.</span></span>|  
|`MDRefToDefNone`|<span data-ttu-id="e66ad-111">Určuje, že žádné odkazované položky, které mají být převedeny na definice.</span><span class="sxs-lookup"><span data-stu-id="e66ad-111">Specifies that no referenced items should be converted to definitions.</span></span>|  
|`MDTypeRefToDef`|<span data-ttu-id="e66ad-112">Určuje, že by měl pouze odkazy na typ převést na typ definice.</span><span class="sxs-lookup"><span data-stu-id="e66ad-112">Specifies that only type references should be converted to type definitions.</span></span>|  
|`MDMemberRefToDef`|<span data-ttu-id="e66ad-113">Určuje, že pouze odkazy na členy mají být převedeny na definice.</span><span class="sxs-lookup"><span data-stu-id="e66ad-113">Specifies that only member references should be converted to definitions.</span></span> <span data-ttu-id="e66ad-114">To znamená odkazy na členy mají být převedeny na definice metod nebo definice pole.</span><span class="sxs-lookup"><span data-stu-id="e66ad-114">That is, member references should be converted to either method definitions or field definitions.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e66ad-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e66ad-115">Requirements</span></span>  
 <span data-ttu-id="e66ad-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e66ad-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e66ad-117">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="e66ad-117">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="e66ad-118">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e66ad-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e66ad-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e66ad-119">See also</span></span>

- [<span data-ttu-id="e66ad-120">Výčty metadat</span><span class="sxs-lookup"><span data-stu-id="e66ad-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
