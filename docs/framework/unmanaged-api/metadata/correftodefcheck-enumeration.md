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
ms.openlocfilehash: ce6f5993b9c1aeb63e121b3567ee468cea1c9318
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007517"
---
# <a name="correftodefcheck-enumeration"></a><span data-ttu-id="f0ee3-102">CorRefToDefCheck – výčet</span><span class="sxs-lookup"><span data-stu-id="f0ee3-102">CorRefToDefCheck Enumeration</span></span>
<span data-ttu-id="f0ee3-103">Určuje příznaky pro řízení, které odkazované položky jsou převedeny na jejich definice za účelem optimalizace kódu.</span><span class="sxs-lookup"><span data-stu-id="f0ee3-103">Specifies flags to control which referenced items are converted to their definitions in order to optimize the code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0ee3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0ee3-104">Syntax</span></span>  
  
```cpp  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a><span data-ttu-id="f0ee3-105">Členové</span><span class="sxs-lookup"><span data-stu-id="f0ee3-105">Members</span></span>  
  
|<span data-ttu-id="f0ee3-106">Člen</span><span class="sxs-lookup"><span data-stu-id="f0ee3-106">Member</span></span>|<span data-ttu-id="f0ee3-107">Description</span><span class="sxs-lookup"><span data-stu-id="f0ee3-107">Description</span></span>|  
|------------|-----------------|  
|`MDRefToDefDefault`|<span data-ttu-id="f0ee3-108">Určuje, že se odkazy na typy a odkazy členů mají převést na definice.</span><span class="sxs-lookup"><span data-stu-id="f0ee3-108">Specifies that type references and member references should be converted to definitions.</span></span> <span data-ttu-id="f0ee3-109">Toto je výchozí hodnota ( `MDTypeRefToDef` &#124; `MDMemberRefToDef` ).</span><span class="sxs-lookup"><span data-stu-id="f0ee3-109">This is the default value (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span></span>|  
|`MDRefToDefAll`|<span data-ttu-id="f0ee3-110">Určuje, že všechny odkazované položky by měly být převedeny na definice.</span><span class="sxs-lookup"><span data-stu-id="f0ee3-110">Specifies that all referenced items should be converted to definitions.</span></span>|  
|`MDRefToDefNone`|<span data-ttu-id="f0ee3-111">Určuje, že žádné odkazované položky by měly být převedeny na definice.</span><span class="sxs-lookup"><span data-stu-id="f0ee3-111">Specifies that no referenced items should be converted to definitions.</span></span>|  
|`MDTypeRefToDef`|<span data-ttu-id="f0ee3-112">Určuje, že se mají převést pouze odkazy typu na definice typu.</span><span class="sxs-lookup"><span data-stu-id="f0ee3-112">Specifies that only type references should be converted to type definitions.</span></span>|  
|`MDMemberRefToDef`|<span data-ttu-id="f0ee3-113">Určuje, že by měly být převedeny pouze odkazy členů na definice.</span><span class="sxs-lookup"><span data-stu-id="f0ee3-113">Specifies that only member references should be converted to definitions.</span></span> <span data-ttu-id="f0ee3-114">To znamená, že odkazy členů by měly být převedeny na buď definice metod, nebo definice polí.</span><span class="sxs-lookup"><span data-stu-id="f0ee3-114">That is, member references should be converted to either method definitions or field definitions.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f0ee3-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f0ee3-115">Requirements</span></span>  
 <span data-ttu-id="f0ee3-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0ee3-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0ee3-117">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="f0ee3-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="f0ee3-118">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0ee3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0ee3-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="f0ee3-119">See also</span></span>

- [<span data-ttu-id="f0ee3-120">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="f0ee3-120">Metadata Enumerations</span></span>](metadata-enumerations.md)
