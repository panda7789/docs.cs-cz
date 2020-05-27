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
ms.openlocfilehash: e8afcb972cab9757458c7032c3678d45c6418fac
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007569"
---
# <a name="corparamattr-enumeration"></a><span data-ttu-id="db464-102">CorParamAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="db464-102">CorParamAttr Enumeration</span></span>
<span data-ttu-id="db464-103">Obsahuje hodnoty, které popisují metadata parametru metody.</span><span class="sxs-lookup"><span data-stu-id="db464-103">Contains values that describe the metadata of a method parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db464-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db464-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="db464-105">Členové</span><span class="sxs-lookup"><span data-stu-id="db464-105">Members</span></span>  
  
|<span data-ttu-id="db464-106">Člen</span><span class="sxs-lookup"><span data-stu-id="db464-106">Member</span></span>|<span data-ttu-id="db464-107">Description</span><span class="sxs-lookup"><span data-stu-id="db464-107">Description</span></span>|  
|------------|-----------------|  
|`pdIn`|<span data-ttu-id="db464-108">Určuje, že se parametr předává do volání metody.</span><span class="sxs-lookup"><span data-stu-id="db464-108">Specifies that the parameter is passed into the method call.</span></span>|  
|`pdOut`|<span data-ttu-id="db464-109">Určuje, že se parametr předává z návratové metody.</span><span class="sxs-lookup"><span data-stu-id="db464-109">Specifies that the parameter is passed from the method return.</span></span>|  
|`pdOptional`|<span data-ttu-id="db464-110">Určuje, že parametr je nepovinný.</span><span class="sxs-lookup"><span data-stu-id="db464-110">Specifies that the parameter is optional.</span></span>|  
|`pdReservedMask`|<span data-ttu-id="db464-111">Vyhrazeno pro interní použití modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="db464-111">Reserved for internal use by the common language runtime.</span></span>|  
|`pdHasDefault`|<span data-ttu-id="db464-112">Určuje, že parametr má výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="db464-112">Specifies that the parameter has a default value.</span></span>|  
|`pdHasFieldMarshal`|<span data-ttu-id="db464-113">Určuje, že má parametr zařazovací informace.</span><span class="sxs-lookup"><span data-stu-id="db464-113">Specifies that the parameter has marshaling information.</span></span>|  
|`pdUnused`|<span data-ttu-id="db464-114">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="db464-114">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="db464-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="db464-115">Requirements</span></span>  
 <span data-ttu-id="db464-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db464-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db464-117">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="db464-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="db464-118">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db464-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db464-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="db464-119">See also</span></span>

- [<span data-ttu-id="db464-120">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="db464-120">Metadata Enumerations</span></span>](metadata-enumerations.md)
