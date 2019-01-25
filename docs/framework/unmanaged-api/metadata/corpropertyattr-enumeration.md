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
ms.openlocfilehash: 713913fa046fc1bef12b8849ac82e4399a8dc534
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577576"
---
# <a name="corpropertyattr-enumeration"></a><span data-ttu-id="66c16-102">CorPropertyAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="66c16-102">CorPropertyAttr Enumeration</span></span>
<span data-ttu-id="66c16-103">Obsahuje hodnoty, které popisují metadata vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="66c16-103">Contains values that describe the metadata of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66c16-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66c16-104">Syntax</span></span>  
  
```  
typedef enum CorPropertyAttr {  
  
    prSpecialName           =   0x0200,   
    prReservedMask          =   0xf400,  
    prRTSpecialName         =   0x0400,  
    prHasDefault            =   0x1000,  
    prUnused                =   0xe9ff  
  
} CorPropertyAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="66c16-105">Členové</span><span class="sxs-lookup"><span data-stu-id="66c16-105">Members</span></span>  
  
|<span data-ttu-id="66c16-106">Člen</span><span class="sxs-lookup"><span data-stu-id="66c16-106">Member</span></span>|<span data-ttu-id="66c16-107">Popis</span><span class="sxs-lookup"><span data-stu-id="66c16-107">Description</span></span>|  
|------------|-----------------|  
|`prSpecialName`|<span data-ttu-id="66c16-108">Určuje, že vlastnost je speciální a který odpovídá názvu jak.</span><span class="sxs-lookup"><span data-stu-id="66c16-108">Specifies that the property is special, and that its name describes how.</span></span>|  
|`prReservedMask`|<span data-ttu-id="66c16-109">Modul common language runtime vyhrazené pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="66c16-109">Reserved for internal use by the common language runtime.</span></span>|  
|`prRTSpecialName`|<span data-ttu-id="66c16-110">Určuje, že common language runtime metadata interních rozhraních API by měla kontrolovat kódování názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="66c16-110">Specifies that the common language runtime metadata internal APIs should check the encoding of the property name.</span></span>|  
|`prHasDefault`|<span data-ttu-id="66c16-111">Určuje, zda vlastnost má výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="66c16-111">Specifies that the property has a default value.</span></span>|  
|`prUnused`|<span data-ttu-id="66c16-112">Nevyužité.</span><span class="sxs-lookup"><span data-stu-id="66c16-112">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="66c16-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66c16-113">Requirements</span></span>  
 <span data-ttu-id="66c16-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66c16-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66c16-115">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="66c16-115">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="66c16-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66c16-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66c16-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66c16-117">See also</span></span>
- [<span data-ttu-id="66c16-118">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="66c16-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
