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
ms.openlocfilehash: 2ae87dd4538a9a8e88591f498c0ce77b51bfa852
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781624"
---
# <a name="correftodefcheck-enumeration"></a><span data-ttu-id="712aa-102">CorRefToDefCheck – výčet</span><span class="sxs-lookup"><span data-stu-id="712aa-102">CorRefToDefCheck Enumeration</span></span>
<span data-ttu-id="712aa-103">Určuje příznaky do ovládacího prvku odkazované položky, které jsou převedeny na jejich definice, aby bylo možné optimalizovat kód.</span><span class="sxs-lookup"><span data-stu-id="712aa-103">Specifies flags to control which referenced items are converted to their definitions in order to optimize the code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="712aa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="712aa-104">Syntax</span></span>  
  
```cpp  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a><span data-ttu-id="712aa-105">Členové</span><span class="sxs-lookup"><span data-stu-id="712aa-105">Members</span></span>  
  
|<span data-ttu-id="712aa-106">Člen</span><span class="sxs-lookup"><span data-stu-id="712aa-106">Member</span></span>|<span data-ttu-id="712aa-107">Popis</span><span class="sxs-lookup"><span data-stu-id="712aa-107">Description</span></span>|  
|------------|-----------------|  
|`MDRefToDefDefault`|<span data-ttu-id="712aa-108">Určuje typ odkazy a odkazy na členy mají být převedeny do definic.</span><span class="sxs-lookup"><span data-stu-id="712aa-108">Specifies that type references and member references should be converted to definitions.</span></span> <span data-ttu-id="712aa-109">Toto je výchozí hodnota (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span><span class="sxs-lookup"><span data-stu-id="712aa-109">This is the default value (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span></span>|  
|`MDRefToDefAll`|<span data-ttu-id="712aa-110">Určuje, zda všechny odkazované položky mají být převedeny na definice.</span><span class="sxs-lookup"><span data-stu-id="712aa-110">Specifies that all referenced items should be converted to definitions.</span></span>|  
|`MDRefToDefNone`|<span data-ttu-id="712aa-111">Určuje, že žádné odkazované položky, které mají být převedeny na definice.</span><span class="sxs-lookup"><span data-stu-id="712aa-111">Specifies that no referenced items should be converted to definitions.</span></span>|  
|`MDTypeRefToDef`|<span data-ttu-id="712aa-112">Určuje, že by měl pouze odkazy na typ převést na typ definice.</span><span class="sxs-lookup"><span data-stu-id="712aa-112">Specifies that only type references should be converted to type definitions.</span></span>|  
|`MDMemberRefToDef`|<span data-ttu-id="712aa-113">Určuje, že pouze odkazy na členy mají být převedeny na definice.</span><span class="sxs-lookup"><span data-stu-id="712aa-113">Specifies that only member references should be converted to definitions.</span></span> <span data-ttu-id="712aa-114">To znamená odkazy na členy mají být převedeny na definice metod nebo definice pole.</span><span class="sxs-lookup"><span data-stu-id="712aa-114">That is, member references should be converted to either method definitions or field definitions.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="712aa-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="712aa-115">Requirements</span></span>  
 <span data-ttu-id="712aa-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="712aa-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="712aa-117">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="712aa-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="712aa-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="712aa-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="712aa-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="712aa-119">See also</span></span>

- [<span data-ttu-id="712aa-120">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="712aa-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
