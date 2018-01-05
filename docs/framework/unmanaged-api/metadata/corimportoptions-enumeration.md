---
title: "CorImportOptions – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorImportOptions
api_location: mscoree.dll
api_type: COM
f1_keywords: CorImportOptions
helpviewer_keywords: CorImportOptions enumeration [.NET Framework metadata]
ms.assetid: 4e5d03cb-97c9-4ff4-8dbd-17d94ee374d3
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e9af7bbb6dd7cfa488f72ec99f9cfd848f04e72f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corimportoptions-enumeration"></a><span data-ttu-id="fb93b-102">CorImportOptions – výčet</span><span class="sxs-lookup"><span data-stu-id="fb93b-102">CorImportOptions Enumeration</span></span>
<span data-ttu-id="fb93b-103">Obsahuje příznak hodnoty, které řídí chování při import sestavení v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="fb93b-103">Contains flag values that control the behavior during importation of an assembly outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb93b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb93b-104">Syntax</span></span>  
  
```  
typedef enum CorImportOptions {  
  
    MDImportOptionDefault                = 0x00000000,  
    MDImportOptionAll                    = 0xFFFFFFFF,  
    MDImportOptionAllTypeDefs            = 0x00000001,  
    MDImportOptionAllMethodDefs          = 0x00000002,  
    MDImportOptionAllFieldDefs           = 0x00000004,  
    MDImportOptionAllProperties          = 0x00000008,  
    MDImportOptionAllEvents              = 0x00000010,  
    MDImportOptionAllCustomAttributes    = 0x00000020,  
    MDImportOptionAllExportedTypes       = 0x00000040  
  
} CorImportOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="fb93b-105">Členové</span><span class="sxs-lookup"><span data-stu-id="fb93b-105">Members</span></span>  
  
|<span data-ttu-id="fb93b-106">Člen</span><span class="sxs-lookup"><span data-stu-id="fb93b-106">Member</span></span>|<span data-ttu-id="fb93b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="fb93b-107">Description</span></span>|  
|------------|-----------------|  
|`MDImportOptionDefault`|<span data-ttu-id="fb93b-108">Určuje výchozí chování, které se mají přeskočit odstraněné záznamy.</span><span class="sxs-lookup"><span data-stu-id="fb93b-108">Indicates the default behavior, which is to skip deleted records.</span></span>|  
|`MDImportOptionAll`|<span data-ttu-id="fb93b-109">Označuje, že všechna metadata ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="fb93b-109">Indicates that all metadata should be enumerated.</span></span>|  
|`MDImportOptionAllTypeDefs`|<span data-ttu-id="fb93b-110">Označuje, že všechny definice TypeDef, včetně odstraněné ty ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="fb93b-110">Indicates that all TypeDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllMethodDefs`|<span data-ttu-id="fb93b-111">Označuje, že všechny MethodDefs, včetně odstraněné ty ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="fb93b-111">Indicates that all MethodDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllFieldDefs`|<span data-ttu-id="fb93b-112">Označuje, že všechny FieldDefs, včetně odstraněné ty ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="fb93b-112">Indicates that all FieldDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllProperties`|<span data-ttu-id="fb93b-113">Označuje, že všechny PropertyDefs, včetně odstraněné ty ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="fb93b-113">Indicates that all PropertyDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllEvents`|<span data-ttu-id="fb93b-114">Označuje, že všechny EventDefs, včetně odstraněné ty ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="fb93b-114">Indicates that all EventDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllCustomAttributes`|<span data-ttu-id="fb93b-115">Označuje, že všech vlastních atributů, včetně odstraněné ty ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="fb93b-115">Indicates that all custom attributes, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllExportedTypes`|<span data-ttu-id="fb93b-116">Označuje, že všechny exportovaný typů, včetně odstraněné ty ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="fb93b-116">Indicates that all exported types, including deleted ones, should be enumerated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fb93b-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fb93b-117">Requirements</span></span>  
 <span data-ttu-id="fb93b-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb93b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb93b-119">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="fb93b-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="fb93b-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb93b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb93b-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb93b-121">See Also</span></span>  
 [<span data-ttu-id="fb93b-122">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="fb93b-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
