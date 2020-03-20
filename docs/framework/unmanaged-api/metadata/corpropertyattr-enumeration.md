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
ms.openlocfilehash: 95a798d662b44cf2e088af84d3b1eec97da8e7fb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177947"
---
# <a name="corpropertyattr-enumeration"></a><span data-ttu-id="67e32-102">CorPropertyAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="67e32-102">CorPropertyAttr Enumeration</span></span>
<span data-ttu-id="67e32-103">Obsahuje hodnoty, které popisují metadata vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="67e32-103">Contains values that describe the metadata of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67e32-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67e32-104">Syntax</span></span>  
  
```cpp  
typedef enum CorPropertyAttr {  
  
    prSpecialName           =   0x0200,
    prReservedMask          =   0xf400,  
    prRTSpecialName         =   0x0400,  
    prHasDefault            =   0x1000,  
    prUnused                =   0xe9ff  
  
} CorPropertyAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="67e32-105">Členové</span><span class="sxs-lookup"><span data-stu-id="67e32-105">Members</span></span>  
  
|<span data-ttu-id="67e32-106">Člen</span><span class="sxs-lookup"><span data-stu-id="67e32-106">Member</span></span>|<span data-ttu-id="67e32-107">Popis</span><span class="sxs-lookup"><span data-stu-id="67e32-107">Description</span></span>|  
|------------|-----------------|  
|`prSpecialName`|<span data-ttu-id="67e32-108">Určuje, že vlastnost je zvláštní a že její název popisuje, jak.</span><span class="sxs-lookup"><span data-stu-id="67e32-108">Specifies that the property is special, and that its name describes how.</span></span>|  
|`prReservedMask`|<span data-ttu-id="67e32-109">Vyhrazeno pro interní použití běžným jazykem runtime.</span><span class="sxs-lookup"><span data-stu-id="67e32-109">Reserved for internal use by the common language runtime.</span></span>|  
|`prRTSpecialName`|<span data-ttu-id="67e32-110">Určuje, že interní rozhraní API metadat modulu RUNTime s běžným jazykem by měla zkontrolovat kódování názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="67e32-110">Specifies that the common language runtime metadata internal APIs should check the encoding of the property name.</span></span>|  
|`prHasDefault`|<span data-ttu-id="67e32-111">Určuje, že vlastnost má výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="67e32-111">Specifies that the property has a default value.</span></span>|  
|`prUnused`|<span data-ttu-id="67e32-112">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="67e32-112">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="67e32-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="67e32-113">Requirements</span></span>  
 <span data-ttu-id="67e32-114">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67e32-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67e32-115">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="67e32-115">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="67e32-116">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67e32-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67e32-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="67e32-117">See also</span></span>

- [<span data-ttu-id="67e32-118">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="67e32-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
