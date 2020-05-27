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
ms.openlocfilehash: 1572c206f4a5a5fe0fd189ca84d0bcda2249c6d4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007647"
---
# <a name="cormethodsemanticsattr-enumeration"></a><span data-ttu-id="df7e3-102">CorMethodSemanticsAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="df7e3-102">CorMethodSemanticsAttr Enumeration</span></span>
<span data-ttu-id="df7e3-103">Obsahuje hodnoty, které popisují vztah mezi metodou a přidruženou vlastností nebo událostí.</span><span class="sxs-lookup"><span data-stu-id="df7e3-103">Contains values that describe the relationship between a method and an associated property or event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df7e3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df7e3-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="df7e3-105">Členové</span><span class="sxs-lookup"><span data-stu-id="df7e3-105">Members</span></span>  
  
|<span data-ttu-id="df7e3-106">Člen</span><span class="sxs-lookup"><span data-stu-id="df7e3-106">Member</span></span>|<span data-ttu-id="df7e3-107">Description</span><span class="sxs-lookup"><span data-stu-id="df7e3-107">Description</span></span>|  
|------------|-----------------|  
|`msSetter`|<span data-ttu-id="df7e3-108">Určuje, že metoda je `set` přístupná pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="df7e3-108">Specifies that the method is a `set` accessor for a property.</span></span>|  
|`msGetter`|<span data-ttu-id="df7e3-109">Určuje, že metoda je `get` přístupná pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="df7e3-109">Specifies that the method is a `get` accessor for a property.</span></span>|  
|`msOther`|<span data-ttu-id="df7e3-110">Určuje, že metoda má relaci k vlastnosti nebo jiné události, než je zde definována.</span><span class="sxs-lookup"><span data-stu-id="df7e3-110">Specifies that the method has a relationship to a property or an event other than those defined here.</span></span>|  
|`msAddOn`|<span data-ttu-id="df7e3-111">Určuje, že metoda přidá metody obslužné rutiny pro událost.</span><span class="sxs-lookup"><span data-stu-id="df7e3-111">Specifies that the method adds handler methods for an event.</span></span>|  
|`msRemoveOn`|<span data-ttu-id="df7e3-112">Určuje, že metoda odebere metody obslužné rutiny pro událost.</span><span class="sxs-lookup"><span data-stu-id="df7e3-112">Specifies that the method removes handler methods for an event.</span></span>|  
|`msFire`|<span data-ttu-id="df7e3-113">Určuje, že metoda vyvolá událost.</span><span class="sxs-lookup"><span data-stu-id="df7e3-113">Specifies that the method raises an event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="df7e3-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="df7e3-114">Requirements</span></span>  
 <span data-ttu-id="df7e3-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df7e3-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df7e3-116">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="df7e3-116">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="df7e3-117">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df7e3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df7e3-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="df7e3-118">See also</span></span>

- [<span data-ttu-id="df7e3-119">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="df7e3-119">Metadata Enumerations</span></span>](metadata-enumerations.md)
