---
title: CorPropertyAttr – výčet
ms.date: 03/30/2017
api_name:
- CorPropertyAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPropertyAttr
helpviewer_keywords:
- CorPropertyAttr enumeration [.NET Framework metadata]
ms.assetid: 58ac8202-854d-4efd-acfb-d2da8b446e12
topic_type:
- apiref
ms.openlocfilehash: b6651f30e0df3a5ffc29d310b9067e76761dcf01
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007530"
---
# <a name="corpropertyattr-enumeration"></a><span data-ttu-id="27025-102">CorPropertyAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="27025-102">CorPropertyAttr Enumeration</span></span>
<span data-ttu-id="27025-103">Obsahuje hodnoty, které popisují metadata vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="27025-103">Contains values that describe the metadata of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27025-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27025-104">Syntax</span></span>  
  
```cpp  
typedef enum CorPropertyAttr {  
  
    prSpecialName           =   0x0200,
    prReservedMask          =   0xf400,  
    prRTSpecialName         =   0x0400,  
    prHasDefault            =   0x1000,  
    prUnused                =   0xe9ff  
  
} CorPropertyAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="27025-105">Členové</span><span class="sxs-lookup"><span data-stu-id="27025-105">Members</span></span>  
  
|<span data-ttu-id="27025-106">Člen</span><span class="sxs-lookup"><span data-stu-id="27025-106">Member</span></span>|<span data-ttu-id="27025-107">Description</span><span class="sxs-lookup"><span data-stu-id="27025-107">Description</span></span>|  
|------------|-----------------|  
|`prSpecialName`|<span data-ttu-id="27025-108">Určuje, že vlastnost je zvláštní a že její název popisuje, jak.</span><span class="sxs-lookup"><span data-stu-id="27025-108">Specifies that the property is special, and that its name describes how.</span></span>|  
|`prReservedMask`|<span data-ttu-id="27025-109">Vyhrazeno pro interní použití modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="27025-109">Reserved for internal use by the common language runtime.</span></span>|  
|`prRTSpecialName`|<span data-ttu-id="27025-110">Určuje, že vnitřní rozhraní API pro Common Language Runtime metadata by měla kontrolovat kódování názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="27025-110">Specifies that the common language runtime metadata internal APIs should check the encoding of the property name.</span></span>|  
|`prHasDefault`|<span data-ttu-id="27025-111">Určuje, že vlastnost má výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="27025-111">Specifies that the property has a default value.</span></span>|  
|`prUnused`|<span data-ttu-id="27025-112">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="27025-112">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="27025-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="27025-113">Requirements</span></span>  
 <span data-ttu-id="27025-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27025-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27025-115">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="27025-115">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="27025-116">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27025-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27025-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="27025-117">See also</span></span>

- [<span data-ttu-id="27025-118">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="27025-118">Metadata Enumerations</span></span>](metadata-enumerations.md)
