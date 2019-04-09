---
title: CorUnmanagedCallingConvention – výčet
ms.date: 03/30/2017
api_name:
- CorUnmanagedCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorUnmanagedCallingConvention
helpviewer_keywords:
- CorUnmanagedCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 83058790-160b-4703-a5eb-74b66acbdfa9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ff308a81282a1cc14c35583daf9cbb057149e556
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178448"
---
# <a name="corunmanagedcallingconvention-enumeration"></a><span data-ttu-id="e6b7a-102">CorUnmanagedCallingConvention – výčet</span><span class="sxs-lookup"><span data-stu-id="e6b7a-102">CorUnmanagedCallingConvention Enumeration</span></span>
<span data-ttu-id="e6b7a-103">Určuje konvence volání nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="e6b7a-103">Specifies the calling conventions for unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6b7a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6b7a-104">Syntax</span></span>  
  
```  
typedef enum CorUnmanagedCallingConvention {  
  
    IMAGE_CEE_UNMANAGED_CALLCONV_C         = 0x1,  
    IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL   = 0x2,  
    IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL  = 0x3,  
    IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL  = 0x4,  
  
    IMAGE_CEE_CS_CALLCONV_C                = 0x1,  
    IMAGE_CEE_CS_CALLCONV_STDCALL          = 0x2,  
    IMAGE_CEE_CS_CALLCONV_THISCALL         = 0x3,  
    IMAGE_CEE_CS_CALLCONV_FASTCALL         = 0x4  
  
} CorUnmanagedCallingConvention;  
```  
  
## <a name="members"></a><span data-ttu-id="e6b7a-105">Členové</span><span class="sxs-lookup"><span data-stu-id="e6b7a-105">Members</span></span>  
  
|<span data-ttu-id="e6b7a-106">Člen</span><span class="sxs-lookup"><span data-stu-id="e6b7a-106">Member</span></span>|<span data-ttu-id="e6b7a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e6b7a-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|<span data-ttu-id="e6b7a-108">C jazykové konvence volání.</span><span class="sxs-lookup"><span data-stu-id="e6b7a-108">The C language calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|<span data-ttu-id="e6b7a-109">Standardní konvence volání.</span><span class="sxs-lookup"><span data-stu-id="e6b7a-109">The standard calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|<span data-ttu-id="e6b7a-110">"Tento" konvence volání.</span><span class="sxs-lookup"><span data-stu-id="e6b7a-110">The "this" calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|<span data-ttu-id="e6b7a-111">"Rychlé" konvence volání.</span><span class="sxs-lookup"><span data-stu-id="e6b7a-111">The "fast" calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_C`|<span data-ttu-id="e6b7a-112">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="e6b7a-112">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|<span data-ttu-id="e6b7a-113">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="e6b7a-113">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|<span data-ttu-id="e6b7a-114">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="e6b7a-114">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|<span data-ttu-id="e6b7a-115">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="e6b7a-115">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6b7a-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e6b7a-116">Remarks</span></span>  
 <span data-ttu-id="e6b7a-117">Modul CLR nepodporuje "rychlé" konvence volání v rozhraní .NET Framework verze 1.0.</span><span class="sxs-lookup"><span data-stu-id="e6b7a-117">The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6b7a-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e6b7a-118">Requirements</span></span>  
 <span data-ttu-id="e6b7a-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6b7a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6b7a-120">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="e6b7a-120">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="e6b7a-121">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e6b7a-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e6b7a-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e6b7a-122">See also</span></span>

- [<span data-ttu-id="e6b7a-123">Výčty metadat</span><span class="sxs-lookup"><span data-stu-id="e6b7a-123">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
