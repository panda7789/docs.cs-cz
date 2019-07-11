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
ms.openlocfilehash: 4b09ccfdb33c9853ed97005461f2288f1e7e6fd1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781751"
---
# <a name="cormethodsemanticsattr-enumeration"></a><span data-ttu-id="63156-102">CorMethodSemanticsAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="63156-102">CorMethodSemanticsAttr Enumeration</span></span>
<span data-ttu-id="63156-103">Obsahuje hodnoty, které popisují vztah mezi metodu a přidružené vlastnosti nebo události.</span><span class="sxs-lookup"><span data-stu-id="63156-103">Contains values that describe the relationship between a method and an associated property or event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63156-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63156-104">Syntax</span></span>  
  
```cpp  
typedef enum CorMethodSemanticsAttr {  
  
    msSetter    =   0x0001,  
    msGetter    =   0x0002,  
    msOther     =   0x0004,  
    msAddOn     =   0x0008,  
    msRemoveOn  =   0x0010,  
    msFire      =   0x0020,  
  
} CorMethodSemanticsAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="63156-105">Členové</span><span class="sxs-lookup"><span data-stu-id="63156-105">Members</span></span>  
  
|<span data-ttu-id="63156-106">Člen</span><span class="sxs-lookup"><span data-stu-id="63156-106">Member</span></span>|<span data-ttu-id="63156-107">Popis</span><span class="sxs-lookup"><span data-stu-id="63156-107">Description</span></span>|  
|------------|-----------------|  
|`msSetter`|<span data-ttu-id="63156-108">Určuje, že metoda je `set` přistupujícího objektu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="63156-108">Specifies that the method is a `set` accessor for a property.</span></span>|  
|`msGetter`|<span data-ttu-id="63156-109">Určuje, že metoda je `get` přistupujícího objektu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="63156-109">Specifies that the method is a `get` accessor for a property.</span></span>|  
|`msOther`|<span data-ttu-id="63156-110">Určuje, že tato metoda má vztah k vlastnosti nebo události než ty, které jsou zde definovány.</span><span class="sxs-lookup"><span data-stu-id="63156-110">Specifies that the method has a relationship to a property or an event other than those defined here.</span></span>|  
|`msAddOn`|<span data-ttu-id="63156-111">Určuje, že metoda přidá metody obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="63156-111">Specifies that the method adds handler methods for an event.</span></span>|  
|`msRemoveOn`|<span data-ttu-id="63156-112">Určuje, že metoda odebere metody obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="63156-112">Specifies that the method removes handler methods for an event.</span></span>|  
|`msFire`|<span data-ttu-id="63156-113">Určuje, že metoda vyvolá událost.</span><span class="sxs-lookup"><span data-stu-id="63156-113">Specifies that the method raises an event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="63156-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="63156-114">Requirements</span></span>  
 <span data-ttu-id="63156-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63156-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63156-116">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="63156-116">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="63156-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63156-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63156-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63156-118">See also</span></span>

- [<span data-ttu-id="63156-119">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="63156-119">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
