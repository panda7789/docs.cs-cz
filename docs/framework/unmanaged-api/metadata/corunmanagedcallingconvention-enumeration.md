---
title: "CorUnmanagedCallingConvention – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorUnmanagedCallingConvention
api_location: mscoree.dll
api_type: COM
f1_keywords: CorUnmanagedCallingConvention
helpviewer_keywords: CorUnmanagedCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 83058790-160b-4703-a5eb-74b66acbdfa9
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f66cb036de8450d4c1b3431b92487260956d47f0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="corunmanagedcallingconvention-enumeration"></a><span data-ttu-id="00bf2-102">CorUnmanagedCallingConvention – výčet</span><span class="sxs-lookup"><span data-stu-id="00bf2-102">CorUnmanagedCallingConvention Enumeration</span></span>
<span data-ttu-id="00bf2-103">Určuje konvencí volání nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="00bf2-103">Specifies the calling conventions for unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00bf2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00bf2-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="00bf2-105">Členové</span><span class="sxs-lookup"><span data-stu-id="00bf2-105">Members</span></span>  
  
|<span data-ttu-id="00bf2-106">Člen</span><span class="sxs-lookup"><span data-stu-id="00bf2-106">Member</span></span>|<span data-ttu-id="00bf2-107">Popis</span><span class="sxs-lookup"><span data-stu-id="00bf2-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|<span data-ttu-id="00bf2-108">Jazyk C volání konvence.</span><span class="sxs-lookup"><span data-stu-id="00bf2-108">The C language calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|<span data-ttu-id="00bf2-109">Standardní konvence volání.</span><span class="sxs-lookup"><span data-stu-id="00bf2-109">The standard calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|<span data-ttu-id="00bf2-110">"Tato" konvence volání.</span><span class="sxs-lookup"><span data-stu-id="00bf2-110">The "this" calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|<span data-ttu-id="00bf2-111">"Rychlé" konvence volání.</span><span class="sxs-lookup"><span data-stu-id="00bf2-111">The "fast" calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_C`|<span data-ttu-id="00bf2-112">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="00bf2-112">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|<span data-ttu-id="00bf2-113">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="00bf2-113">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|<span data-ttu-id="00bf2-114">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="00bf2-114">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|<span data-ttu-id="00bf2-115">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="00bf2-115">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00bf2-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="00bf2-116">Remarks</span></span>  
 <span data-ttu-id="00bf2-117">Modul CLR nepodporuje "rychlé" konvence volání v rozhraní .NET Framework verze 1.0.</span><span class="sxs-lookup"><span data-stu-id="00bf2-117">The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00bf2-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="00bf2-118">Requirements</span></span>  
 <span data-ttu-id="00bf2-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00bf2-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00bf2-120">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="00bf2-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="00bf2-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00bf2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00bf2-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="00bf2-122">See Also</span></span>  
 [<span data-ttu-id="00bf2-123">Výčty metadat</span><span class="sxs-lookup"><span data-stu-id="00bf2-123">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
