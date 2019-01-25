---
title: CorParamAttr – výčet
ms.date: 03/30/2017
api_name:
- CorParamAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorParamAttr
helpviewer_keywords:
- CorParamAttr enumeration [.NET Framework metadata]
ms.assetid: a7ff90ad-dad8-48e8-917d-4aa9a118cbc8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7d07c6de47038d5c52d76ad8ca8e0a5684551d59
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491464"
---
# <a name="corparamattr-enumeration"></a><span data-ttu-id="66a74-102">CorParamAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="66a74-102">CorParamAttr Enumeration</span></span>
<span data-ttu-id="66a74-103">Obsahuje hodnoty, které popisují metadata parametru metody.</span><span class="sxs-lookup"><span data-stu-id="66a74-103">Contains values that describe the metadata of a method parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66a74-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66a74-104">Syntax</span></span>  
  
```  
typedef enum CorParamAttr {  
  
    pdIn                        =   0x0001,  
    pdOut                       =   0x0002,  
    pdOptional                  =   0x0010,  
  
    pdReservedMask              =   0xf000,  
    pdHasDefault                =   0x1000,  
    pdHasFieldMarshal           =   0x2000,  
  
    pdUnused                    =   0xcfe0  
  
} CorParamAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="66a74-105">Členové</span><span class="sxs-lookup"><span data-stu-id="66a74-105">Members</span></span>  
  
|<span data-ttu-id="66a74-106">Člen</span><span class="sxs-lookup"><span data-stu-id="66a74-106">Member</span></span>|<span data-ttu-id="66a74-107">Popis</span><span class="sxs-lookup"><span data-stu-id="66a74-107">Description</span></span>|  
|------------|-----------------|  
|`pdIn`|<span data-ttu-id="66a74-108">Určuje, že parametr se předává do volání metody.</span><span class="sxs-lookup"><span data-stu-id="66a74-108">Specifies that the parameter is passed into the method call.</span></span>|  
|`pdOut`|<span data-ttu-id="66a74-109">Určuje, že parametr je předán z metody návratovou.</span><span class="sxs-lookup"><span data-stu-id="66a74-109">Specifies that the parameter is passed from the method return.</span></span>|  
|`pdOptional`|<span data-ttu-id="66a74-110">Určuje, že se jedná o volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="66a74-110">Specifies that the parameter is optional.</span></span>|  
|`pdReservedMask`|<span data-ttu-id="66a74-111">Modul common language runtime vyhrazené pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="66a74-111">Reserved for internal use by the common language runtime.</span></span>|  
|`pdHasDefault`|<span data-ttu-id="66a74-112">Určuje, že parametr má výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="66a74-112">Specifies that the parameter has a default value.</span></span>|  
|`pdHasFieldMarshal`|<span data-ttu-id="66a74-113">Určuje, že parametr obsahuje zařazovací informace.</span><span class="sxs-lookup"><span data-stu-id="66a74-113">Specifies that the parameter has marshaling information.</span></span>|  
|`pdUnused`|<span data-ttu-id="66a74-114">Nevyužité.</span><span class="sxs-lookup"><span data-stu-id="66a74-114">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="66a74-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66a74-115">Requirements</span></span>  
 <span data-ttu-id="66a74-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66a74-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66a74-117">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="66a74-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="66a74-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66a74-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66a74-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66a74-119">See also</span></span>
- [<span data-ttu-id="66a74-120">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="66a74-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
