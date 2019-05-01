---
title: CorCallingConvention – výčet
ms.date: 03/30/2017
api_name:
- CorCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCallingConvention
helpviewer_keywords:
- CorCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 69156fbf-7219-43bf-b4b8-b13f1a2fcb86
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 44a4b5903cec2249eb1e176381fe3d8e600dd5e6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62046108"
---
# <a name="corcallingconvention-enumeration"></a><span data-ttu-id="838ce-102">CorCallingConvention – výčet</span><span class="sxs-lookup"><span data-stu-id="838ce-102">CorCallingConvention Enumeration</span></span>
<span data-ttu-id="838ce-103">Obsahuje hodnoty, které popisují typy konvence volání, které probíhají ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="838ce-103">Contains values that describe the types of calling conventions that are made in managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="838ce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="838ce-104">Syntax</span></span>  
  
```  
typedef enum CorCallingConvention  
{  
    IMAGE_CEE_CS_CALLCONV_DEFAULT       = 0x0,  
  
    IMAGE_CEE_CS_CALLCONV_VARARG        = 0x5,  
    IMAGE_CEE_CS_CALLCONV_FIELD         = 0x6,  
    IMAGE_CEE_CS_CALLCONV_LOCAL_SIG     = 0x7,  
    IMAGE_CEE_CS_CALLCONV_PROPERTY      = 0x8,  
    IMAGE_CEE_CS_CALLCONV_UNMGD         = 0x9,  
    IMAGE_CEE_CS_CALLCONV_GENERICINST   = 0xa,  
    IMAGE_CEE_CS_CALLCONV_NATIVEVARARG  = 0xb,  
    IMAGE_CEE_CS_CALLCONV_MAX           = 0xc,  
  
    IMAGE_CEE_CS_CALLCONV_MASK          = 0x0f,  
    IMAGE_CEE_CS_CALLCONV_HASTHIS       = 0x20,  
    IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS  = 0x40,  
    IMAGE_CEE_CS_CALLCONV_GENERIC       = 0x10  
  
} CorCallingConvention;  
```  
  
## <a name="members"></a><span data-ttu-id="838ce-105">Členové</span><span class="sxs-lookup"><span data-stu-id="838ce-105">Members</span></span>  
  
|<span data-ttu-id="838ce-106">Člen</span><span class="sxs-lookup"><span data-stu-id="838ce-106">Member</span></span>|<span data-ttu-id="838ce-107">Popis</span><span class="sxs-lookup"><span data-stu-id="838ce-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|<span data-ttu-id="838ce-108">Určuje výchozí konvenci volání.</span><span class="sxs-lookup"><span data-stu-id="838ce-108">Indicates a default calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|<span data-ttu-id="838ce-109">Označuje, že tato metoda přebírá proměnný počet parametrů.</span><span class="sxs-lookup"><span data-stu-id="838ce-109">Indicates that the method takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|<span data-ttu-id="838ce-110">Označuje, že volání je k poli.</span><span class="sxs-lookup"><span data-stu-id="838ce-110">Indicates that the call is to a field.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|<span data-ttu-id="838ce-111">Označuje, že volání místní metody.</span><span class="sxs-lookup"><span data-stu-id="838ce-111">Indicates that the call is to a local method.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|<span data-ttu-id="838ce-112">Označuje, že volání na vlastnost.</span><span class="sxs-lookup"><span data-stu-id="838ce-112">Indicates that the call is to a property.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|<span data-ttu-id="838ce-113">Označuje, že je volání nespravovaných.</span><span class="sxs-lookup"><span data-stu-id="838ce-113">Indicates that the call is unmanaged.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|<span data-ttu-id="838ce-114">Určuje instance obecné metody.</span><span class="sxs-lookup"><span data-stu-id="838ce-114">Indicates a generic method instantiation.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|<span data-ttu-id="838ce-115">Označuje volání PInvoke 64-bit na metodu, která přijímá proměnný počet parametrů.</span><span class="sxs-lookup"><span data-stu-id="838ce-115">Indicates a 64-bit PInvoke call to a method that takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|<span data-ttu-id="838ce-116">Popisuje neplatnou hodnotu 4-bit.</span><span class="sxs-lookup"><span data-stu-id="838ce-116">Describes an invalid 4-bit value.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|<span data-ttu-id="838ce-117">Určuje, zda konvence volání je popsán dolní čtyři bity.</span><span class="sxs-lookup"><span data-stu-id="838ce-117">Indicates that the calling convention is described by the bottom four bits.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|<span data-ttu-id="838ce-118">Označuje, že popisuje hlavní verze `this` parametru.</span><span class="sxs-lookup"><span data-stu-id="838ce-118">Indicates that the top bit describes a `this` parameter.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|<span data-ttu-id="838ce-119">Označuje, že `this` parametr je explicitně je popsáno v podpisu.</span><span class="sxs-lookup"><span data-stu-id="838ce-119">Indicates that a `this` parameter is explicitly described in the signature.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|<span data-ttu-id="838ce-120">Označuje signaturu obecné metody pomocí explicitní počet argumentů typu.</span><span class="sxs-lookup"><span data-stu-id="838ce-120">Indicates a generic method signature with an explicit number of type arguments.</span></span> <span data-ttu-id="838ce-121">To předchází počet běžných parametrů.</span><span class="sxs-lookup"><span data-stu-id="838ce-121">This precedes an ordinary parameter count.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="838ce-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="838ce-122">Requirements</span></span>  
 <span data-ttu-id="838ce-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="838ce-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="838ce-124">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="838ce-124">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="838ce-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="838ce-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="838ce-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="838ce-126">See also</span></span>

- [<span data-ttu-id="838ce-127">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="838ce-127">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
