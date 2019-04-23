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
ms.openlocfilehash: f1a0fff266e964b506b2dc7c4030caa54abaa5ed
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59171818"
---
# <a name="corpropertyattr-enumeration"></a><span data-ttu-id="dae47-102">CorPropertyAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="dae47-102">CorPropertyAttr Enumeration</span></span>
<span data-ttu-id="dae47-103">Obsahuje hodnoty, které popisují metadata vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="dae47-103">Contains values that describe the metadata of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dae47-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dae47-104">Syntax</span></span>  
  
```  
typedef enum CorPropertyAttr {  
  
    prSpecialName           =   0x0200,   
    prReservedMask          =   0xf400,  
    prRTSpecialName         =   0x0400,  
    prHasDefault            =   0x1000,  
    prUnused                =   0xe9ff  
  
} CorPropertyAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="dae47-105">Členové</span><span class="sxs-lookup"><span data-stu-id="dae47-105">Members</span></span>  
  
|<span data-ttu-id="dae47-106">Člen</span><span class="sxs-lookup"><span data-stu-id="dae47-106">Member</span></span>|<span data-ttu-id="dae47-107">Popis</span><span class="sxs-lookup"><span data-stu-id="dae47-107">Description</span></span>|  
|------------|-----------------|  
|`prSpecialName`|<span data-ttu-id="dae47-108">Určuje, že vlastnost je speciální a který odpovídá názvu jak.</span><span class="sxs-lookup"><span data-stu-id="dae47-108">Specifies that the property is special, and that its name describes how.</span></span>|  
|`prReservedMask`|<span data-ttu-id="dae47-109">Modul common language runtime vyhrazené pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="dae47-109">Reserved for internal use by the common language runtime.</span></span>|  
|`prRTSpecialName`|<span data-ttu-id="dae47-110">Určuje, že common language runtime metadata interních rozhraních API by měla kontrolovat kódování názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="dae47-110">Specifies that the common language runtime metadata internal APIs should check the encoding of the property name.</span></span>|  
|`prHasDefault`|<span data-ttu-id="dae47-111">Určuje, zda vlastnost má výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="dae47-111">Specifies that the property has a default value.</span></span>|  
|`prUnused`|<span data-ttu-id="dae47-112">Nevyužité.</span><span class="sxs-lookup"><span data-stu-id="dae47-112">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dae47-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dae47-113">Requirements</span></span>  
 <span data-ttu-id="dae47-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dae47-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dae47-115">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="dae47-115">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="dae47-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dae47-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dae47-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dae47-117">See also</span></span>

- [<span data-ttu-id="dae47-118">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="dae47-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
