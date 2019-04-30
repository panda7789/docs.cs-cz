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
ms.openlocfilehash: 97f62b082db11a5f0bb930e33cb47acef76e7a04
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61906295"
---
# <a name="corparamattr-enumeration"></a><span data-ttu-id="f8d5d-102">CorParamAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="f8d5d-102">CorParamAttr Enumeration</span></span>
<span data-ttu-id="f8d5d-103">Obsahuje hodnoty, které popisují metadata parametru metody.</span><span class="sxs-lookup"><span data-stu-id="f8d5d-103">Contains values that describe the metadata of a method parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8d5d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8d5d-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="f8d5d-105">Členové</span><span class="sxs-lookup"><span data-stu-id="f8d5d-105">Members</span></span>  
  
|<span data-ttu-id="f8d5d-106">Člen</span><span class="sxs-lookup"><span data-stu-id="f8d5d-106">Member</span></span>|<span data-ttu-id="f8d5d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f8d5d-107">Description</span></span>|  
|------------|-----------------|  
|`pdIn`|<span data-ttu-id="f8d5d-108">Určuje, že parametr se předává do volání metody.</span><span class="sxs-lookup"><span data-stu-id="f8d5d-108">Specifies that the parameter is passed into the method call.</span></span>|  
|`pdOut`|<span data-ttu-id="f8d5d-109">Určuje, že parametr je předán z metody návratovou.</span><span class="sxs-lookup"><span data-stu-id="f8d5d-109">Specifies that the parameter is passed from the method return.</span></span>|  
|`pdOptional`|<span data-ttu-id="f8d5d-110">Určuje, že se jedná o volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="f8d5d-110">Specifies that the parameter is optional.</span></span>|  
|`pdReservedMask`|<span data-ttu-id="f8d5d-111">Modul common language runtime vyhrazené pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="f8d5d-111">Reserved for internal use by the common language runtime.</span></span>|  
|`pdHasDefault`|<span data-ttu-id="f8d5d-112">Určuje, že parametr má výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f8d5d-112">Specifies that the parameter has a default value.</span></span>|  
|`pdHasFieldMarshal`|<span data-ttu-id="f8d5d-113">Určuje, že parametr obsahuje zařazovací informace.</span><span class="sxs-lookup"><span data-stu-id="f8d5d-113">Specifies that the parameter has marshaling information.</span></span>|  
|`pdUnused`|<span data-ttu-id="f8d5d-114">Nevyužité.</span><span class="sxs-lookup"><span data-stu-id="f8d5d-114">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f8d5d-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f8d5d-115">Requirements</span></span>  
 <span data-ttu-id="f8d5d-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8d5d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8d5d-117">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="f8d5d-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="f8d5d-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8d5d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8d5d-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8d5d-119">See also</span></span>

- [<span data-ttu-id="f8d5d-120">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="f8d5d-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
