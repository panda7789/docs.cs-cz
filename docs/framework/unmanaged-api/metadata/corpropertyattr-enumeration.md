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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 263981708af2e40bd3690a3cd344156488eed0dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442676"
---
# <a name="corpropertyattr-enumeration"></a><span data-ttu-id="8caa4-102">CorPropertyAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="8caa4-102">CorPropertyAttr Enumeration</span></span>
<span data-ttu-id="8caa4-103">Obsahuje hodnoty, které popisují metadata vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8caa4-103">Contains values that describe the metadata of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8caa4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8caa4-104">Syntax</span></span>  
  
```  
typedef enum CorPropertyAttr {  
  
    prSpecialName           =   0x0200,   
    prReservedMask          =   0xf400,  
    prRTSpecialName         =   0x0400,  
    prHasDefault            =   0x1000,  
    prUnused                =   0xe9ff  
  
} CorPropertyAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="8caa4-105">Členové</span><span class="sxs-lookup"><span data-stu-id="8caa4-105">Members</span></span>  
  
|<span data-ttu-id="8caa4-106">Člen</span><span class="sxs-lookup"><span data-stu-id="8caa4-106">Member</span></span>|<span data-ttu-id="8caa4-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8caa4-107">Description</span></span>|  
|------------|-----------------|  
|`prSpecialName`|<span data-ttu-id="8caa4-108">Určuje, zda je vlastnost speciální a že její název popisuje jak.</span><span class="sxs-lookup"><span data-stu-id="8caa4-108">Specifies that the property is special, and that its name describes how.</span></span>|  
|`prReservedMask`|<span data-ttu-id="8caa4-109">Modul common language runtime vyhrazené pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="8caa4-109">Reserved for internal use by the common language runtime.</span></span>|  
|`prRTSpecialName`|<span data-ttu-id="8caa4-110">Určuje, že běžná metadata modulu runtime jazyka interní rozhraní API měli kontrolovat kódování názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8caa4-110">Specifies that the common language runtime metadata internal APIs should check the encoding of the property name.</span></span>|  
|`prHasDefault`|<span data-ttu-id="8caa4-111">Určuje, že tato vlastnost nemá výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8caa4-111">Specifies that the property has a default value.</span></span>|  
|`prUnused`|<span data-ttu-id="8caa4-112">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="8caa4-112">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8caa4-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8caa4-113">Requirements</span></span>  
 <span data-ttu-id="8caa4-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8caa4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8caa4-115">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="8caa4-115">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="8caa4-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8caa4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8caa4-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="8caa4-117">See Also</span></span>  
 [<span data-ttu-id="8caa4-118">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="8caa4-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
