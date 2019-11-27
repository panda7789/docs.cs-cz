---
title: CorImportOptions – výčet
ms.date: 03/30/2017
api_name:
- CorImportOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorImportOptions
helpviewer_keywords:
- CorImportOptions enumeration [.NET Framework metadata]
ms.assetid: 4e5d03cb-97c9-4ff4-8dbd-17d94ee374d3
topic_type:
- apiref
ms.openlocfilehash: 44d1776e2902988353ef4fd58aca20e56203b9da
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442844"
---
# <a name="corimportoptions-enumeration"></a><span data-ttu-id="5cef8-102">CorImportOptions – výčet</span><span class="sxs-lookup"><span data-stu-id="5cef8-102">CorImportOptions Enumeration</span></span>
<span data-ttu-id="5cef8-103">Obsahuje hodnoty příznaků, které řídí chování při dovozu sestavení mimo aktuální rozsah.</span><span class="sxs-lookup"><span data-stu-id="5cef8-103">Contains flag values that control the behavior during importation of an assembly outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cef8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5cef8-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="5cef8-105">Členové</span><span class="sxs-lookup"><span data-stu-id="5cef8-105">Members</span></span>  
  
|<span data-ttu-id="5cef8-106">Člen</span><span class="sxs-lookup"><span data-stu-id="5cef8-106">Member</span></span>|<span data-ttu-id="5cef8-107">Popis</span><span class="sxs-lookup"><span data-stu-id="5cef8-107">Description</span></span>|  
|------------|-----------------|  
|`MDImportOptionDefault`|<span data-ttu-id="5cef8-108">Označuje výchozí chování, které má přeskočit odstraněné záznamy.</span><span class="sxs-lookup"><span data-stu-id="5cef8-108">Indicates the default behavior, which is to skip deleted records.</span></span>|  
|`MDImportOptionAll`|<span data-ttu-id="5cef8-109">Označuje, že by měla být vytvořena výčet všech metadat.</span><span class="sxs-lookup"><span data-stu-id="5cef8-109">Indicates that all metadata should be enumerated.</span></span>|  
|`MDImportOptionAllTypeDefs`|<span data-ttu-id="5cef8-110">Označuje, že by měly být vyčísleny všechny definice typedef, včetně odstraněných.</span><span class="sxs-lookup"><span data-stu-id="5cef8-110">Indicates that all TypeDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllMethodDefs`|<span data-ttu-id="5cef8-111">Označuje, že by měly být vyčísleny všechny MethodDefs, včetně odstraněných.</span><span class="sxs-lookup"><span data-stu-id="5cef8-111">Indicates that all MethodDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllFieldDefs`|<span data-ttu-id="5cef8-112">Označuje, že by měly být vyčísleny všechny FieldDefs, včetně odstraněných.</span><span class="sxs-lookup"><span data-stu-id="5cef8-112">Indicates that all FieldDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllProperties`|<span data-ttu-id="5cef8-113">Označuje, že by měly být vyčísleny všechny PropertyDefs, včetně odstraněných.</span><span class="sxs-lookup"><span data-stu-id="5cef8-113">Indicates that all PropertyDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllEvents`|<span data-ttu-id="5cef8-114">Označuje, že by měly být vyčísleny všechny EventDefs, včetně odstraněných.</span><span class="sxs-lookup"><span data-stu-id="5cef8-114">Indicates that all EventDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllCustomAttributes`|<span data-ttu-id="5cef8-115">Označuje, že by měly být vyčísleny všechny vlastní atributy včetně odstraněných.</span><span class="sxs-lookup"><span data-stu-id="5cef8-115">Indicates that all custom attributes, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllExportedTypes`|<span data-ttu-id="5cef8-116">Označuje, že by se měly vytvořit výčty všech exportovaných typů, včetně odstraněných.</span><span class="sxs-lookup"><span data-stu-id="5cef8-116">Indicates that all exported types, including deleted ones, should be enumerated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5cef8-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5cef8-117">Requirements</span></span>  
 <span data-ttu-id="5cef8-118">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cef8-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cef8-119">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="5cef8-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="5cef8-120">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cef8-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cef8-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5cef8-121">See also</span></span>

- [<span data-ttu-id="5cef8-122">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="5cef8-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
