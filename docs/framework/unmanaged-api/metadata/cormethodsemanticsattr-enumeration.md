---
title: CorMethodSemanticsAttr – výčet
ms.date: 03/30/2017
api_name:
- CorMethodSemanticsAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodSemanticsAttr
helpviewer_keywords:
- CorMethodSemanticsAttr enumeration [.NET Framework metadata]
ms.assetid: ca2af325-eb9d-4a91-90e4-267e45b98611
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5e36cb91c3ef741badb04b54e2b62158ecf6ced1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134495"
---
# <a name="cormethodsemanticsattr-enumeration"></a><span data-ttu-id="3f21b-102">CorMethodSemanticsAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="3f21b-102">CorMethodSemanticsAttr Enumeration</span></span>
<span data-ttu-id="3f21b-103">Obsahuje hodnoty, které popisují vztah mezi metodu a přidružené vlastnosti nebo události.</span><span class="sxs-lookup"><span data-stu-id="3f21b-103">Contains values that describe the relationship between a method and an associated property or event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f21b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f21b-104">Syntax</span></span>  
  
```  
typedef enum CorMethodSemanticsAttr {  
  
    msSetter    =   0x0001,  
    msGetter    =   0x0002,  
    msOther     =   0x0004,  
    msAddOn     =   0x0008,  
    msRemoveOn  =   0x0010,  
    msFire      =   0x0020,  
  
} CorMethodSemanticsAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="3f21b-105">Členové</span><span class="sxs-lookup"><span data-stu-id="3f21b-105">Members</span></span>  
  
|<span data-ttu-id="3f21b-106">Člen</span><span class="sxs-lookup"><span data-stu-id="3f21b-106">Member</span></span>|<span data-ttu-id="3f21b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3f21b-107">Description</span></span>|  
|------------|-----------------|  
|`msSetter`|<span data-ttu-id="3f21b-108">Určuje, že metoda je `set` přistupujícího objektu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3f21b-108">Specifies that the method is a `set` accessor for a property.</span></span>|  
|`msGetter`|<span data-ttu-id="3f21b-109">Určuje, že metoda je `get` přistupujícího objektu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3f21b-109">Specifies that the method is a `get` accessor for a property.</span></span>|  
|`msOther`|<span data-ttu-id="3f21b-110">Určuje, že tato metoda má vztah k vlastnosti nebo události než ty, které jsou zde definovány.</span><span class="sxs-lookup"><span data-stu-id="3f21b-110">Specifies that the method has a relationship to a property or an event other than those defined here.</span></span>|  
|`msAddOn`|<span data-ttu-id="3f21b-111">Určuje, že metoda přidá metody obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="3f21b-111">Specifies that the method adds handler methods for an event.</span></span>|  
|`msRemoveOn`|<span data-ttu-id="3f21b-112">Určuje, že metoda odebere metody obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="3f21b-112">Specifies that the method removes handler methods for an event.</span></span>|  
|`msFire`|<span data-ttu-id="3f21b-113">Určuje, že metoda vyvolá událost.</span><span class="sxs-lookup"><span data-stu-id="3f21b-113">Specifies that the method raises an event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3f21b-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3f21b-114">Requirements</span></span>  
 <span data-ttu-id="3f21b-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f21b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f21b-116">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="3f21b-116">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="3f21b-117">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="3f21b-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3f21b-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3f21b-118">See also</span></span>

- [<span data-ttu-id="3f21b-119">Výčty metadat</span><span class="sxs-lookup"><span data-stu-id="3f21b-119">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
