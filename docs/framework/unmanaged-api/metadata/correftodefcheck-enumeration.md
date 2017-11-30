---
title: "CorRefToDefCheck – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorRefToDefCheck
api_location: mscoree.dll
api_type: COM
f1_keywords: CorRefToDefCheck
helpviewer_keywords: CorRefToDefCheck enumeration [.NET Framework metadata]
ms.assetid: f9a80f1a-55af-4459-b095-8441aae16119
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5144cd3ac261647c04ec7e3e27e28618c94fb439
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="correftodefcheck-enumeration"></a><span data-ttu-id="bd1c7-102">CorRefToDefCheck – výčet</span><span class="sxs-lookup"><span data-stu-id="bd1c7-102">CorRefToDefCheck Enumeration</span></span>
<span data-ttu-id="bd1c7-103">Určuje příznaky tak, aby řízení odkazované položek, které jsou převedeny na jejich definice k optimalizaci kód.</span><span class="sxs-lookup"><span data-stu-id="bd1c7-103">Specifies flags to control which referenced items are converted to their definitions in order to optimize the code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd1c7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd1c7-104">Syntax</span></span>  
  
```  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a><span data-ttu-id="bd1c7-105">Členové</span><span class="sxs-lookup"><span data-stu-id="bd1c7-105">Members</span></span>  
  
|<span data-ttu-id="bd1c7-106">Člen</span><span class="sxs-lookup"><span data-stu-id="bd1c7-106">Member</span></span>|<span data-ttu-id="bd1c7-107">Popis</span><span class="sxs-lookup"><span data-stu-id="bd1c7-107">Description</span></span>|  
|------------|-----------------|  
|`MDRefToDefDefault`|<span data-ttu-id="bd1c7-108">Určuje, že odkazy na typ a odkazy na členy mají být převedeny na definice.</span><span class="sxs-lookup"><span data-stu-id="bd1c7-108">Specifies that type references and member references should be converted to definitions.</span></span> <span data-ttu-id="bd1c7-109">Toto je výchozí hodnota (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span><span class="sxs-lookup"><span data-stu-id="bd1c7-109">This is the default value (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span></span>|  
|`MDRefToDefAll`|<span data-ttu-id="bd1c7-110">Určuje, zda všechny odkazované položky mají být převedeny na definice.</span><span class="sxs-lookup"><span data-stu-id="bd1c7-110">Specifies that all referenced items should be converted to definitions.</span></span>|  
|`MDRefToDefNone`|<span data-ttu-id="bd1c7-111">Určuje, že žádné odkazované položky mají být převedeny na definice.</span><span class="sxs-lookup"><span data-stu-id="bd1c7-111">Specifies that no referenced items should be converted to definitions.</span></span>|  
|`MDTypeRefToDef`|<span data-ttu-id="bd1c7-112">Určuje, že pouze odkazy na typ měli převést na typ definice.</span><span class="sxs-lookup"><span data-stu-id="bd1c7-112">Specifies that only type references should be converted to type definitions.</span></span>|  
|`MDMemberRefToDef`|<span data-ttu-id="bd1c7-113">Určuje, že mají být převedeny pouze člen odkazy na definice.</span><span class="sxs-lookup"><span data-stu-id="bd1c7-113">Specifies that only member references should be converted to definitions.</span></span> <span data-ttu-id="bd1c7-114">To znamená odkazy na členy, které mají být převedeny na metoda definice nebo definice polí.</span><span class="sxs-lookup"><span data-stu-id="bd1c7-114">That is, member references should be converted to either method definitions or field definitions.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bd1c7-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bd1c7-115">Requirements</span></span>  
 <span data-ttu-id="bd1c7-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd1c7-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd1c7-117">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="bd1c7-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="bd1c7-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd1c7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd1c7-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="bd1c7-119">See Also</span></span>  
 [<span data-ttu-id="bd1c7-120">Výčty metadat</span><span class="sxs-lookup"><span data-stu-id="bd1c7-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
