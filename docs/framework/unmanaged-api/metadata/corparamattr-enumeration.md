---
title: "CorParamAttr – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorParamAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CorParamAttr
helpviewer_keywords: CorParamAttr enumeration [.NET Framework metadata]
ms.assetid: a7ff90ad-dad8-48e8-917d-4aa9a118cbc8
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 87afe125536473f99053db7d2fd4ae61fa4017ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corparamattr-enumeration"></a><span data-ttu-id="9ef78-102">CorParamAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="9ef78-102">CorParamAttr Enumeration</span></span>
<span data-ttu-id="9ef78-103">Obsahuje hodnoty, které popisují metadata parametru metody.</span><span class="sxs-lookup"><span data-stu-id="9ef78-103">Contains values that describe the metadata of a method parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ef78-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ef78-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="9ef78-105">Členové</span><span class="sxs-lookup"><span data-stu-id="9ef78-105">Members</span></span>  
  
|<span data-ttu-id="9ef78-106">Člen</span><span class="sxs-lookup"><span data-stu-id="9ef78-106">Member</span></span>|<span data-ttu-id="9ef78-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9ef78-107">Description</span></span>|  
|------------|-----------------|  
|`pdIn`|<span data-ttu-id="9ef78-108">Určuje, že parametr se předává do volání metody.</span><span class="sxs-lookup"><span data-stu-id="9ef78-108">Specifies that the parameter is passed into the method call.</span></span>|  
|`pdOut`|<span data-ttu-id="9ef78-109">Určuje, že parametr se předává z metody návratový.</span><span class="sxs-lookup"><span data-stu-id="9ef78-109">Specifies that the parameter is passed from the method return.</span></span>|  
|`pdOptional`|<span data-ttu-id="9ef78-110">Určuje, zda se jedná o volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="9ef78-110">Specifies that the parameter is optional.</span></span>|  
|`pdReservedMask`|<span data-ttu-id="9ef78-111">Modul common language runtime vyhrazené pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="9ef78-111">Reserved for internal use by the common language runtime.</span></span>|  
|`pdHasDefault`|<span data-ttu-id="9ef78-112">Určuje, že parametr nemá výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9ef78-112">Specifies that the parameter has a default value.</span></span>|  
|`pdHasFieldMarshal`|<span data-ttu-id="9ef78-113">Určuje, zda má parametr zařazování informace.</span><span class="sxs-lookup"><span data-stu-id="9ef78-113">Specifies that the parameter has marshaling information.</span></span>|  
|`pdUnused`|<span data-ttu-id="9ef78-114">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="9ef78-114">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9ef78-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9ef78-115">Requirements</span></span>  
 <span data-ttu-id="9ef78-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ef78-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ef78-117">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="9ef78-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="9ef78-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ef78-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ef78-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="9ef78-119">See Also</span></span>  
 [<span data-ttu-id="9ef78-120">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="9ef78-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
