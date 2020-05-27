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
ms.openlocfilehash: b4c521489f38360d45c2cf8ff3780e057299f0b4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008947"
---
# <a name="corunmanagedcallingconvention-enumeration"></a><span data-ttu-id="a0d4b-102">CorUnmanagedCallingConvention – výčet</span><span class="sxs-lookup"><span data-stu-id="a0d4b-102">CorUnmanagedCallingConvention Enumeration</span></span>
<span data-ttu-id="a0d4b-103">Určuje konvence volání pro nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="a0d4b-103">Specifies the calling conventions for unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0d4b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0d4b-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="a0d4b-105">Členové</span><span class="sxs-lookup"><span data-stu-id="a0d4b-105">Members</span></span>  
  
|<span data-ttu-id="a0d4b-106">Člen</span><span class="sxs-lookup"><span data-stu-id="a0d4b-106">Member</span></span>|<span data-ttu-id="a0d4b-107">Description</span><span class="sxs-lookup"><span data-stu-id="a0d4b-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|<span data-ttu-id="a0d4b-108">Konvence volání jazyka C.</span><span class="sxs-lookup"><span data-stu-id="a0d4b-108">The C language calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|<span data-ttu-id="a0d4b-109">Standardní konvence volání.</span><span class="sxs-lookup"><span data-stu-id="a0d4b-109">The standard calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|<span data-ttu-id="a0d4b-110">Konvence volání "This".</span><span class="sxs-lookup"><span data-stu-id="a0d4b-110">The "this" calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|<span data-ttu-id="a0d4b-111">Konvence volání "Fast".</span><span class="sxs-lookup"><span data-stu-id="a0d4b-111">The "fast" calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_C`|<span data-ttu-id="a0d4b-112">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="a0d4b-112">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|<span data-ttu-id="a0d4b-113">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="a0d4b-113">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|<span data-ttu-id="a0d4b-114">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="a0d4b-114">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|<span data-ttu-id="a0d4b-115">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="a0d4b-115">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0d4b-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a0d4b-116">Remarks</span></span>  
 <span data-ttu-id="a0d4b-117">Modul CLR nepodporuje konvenci volání "Fast" v .NET Framework verze 1,0.</span><span class="sxs-lookup"><span data-stu-id="a0d4b-117">The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0d4b-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a0d4b-118">Requirements</span></span>  
 <span data-ttu-id="a0d4b-119">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0d4b-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0d4b-120">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="a0d4b-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="a0d4b-121">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0d4b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0d4b-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0d4b-122">See also</span></span>

- [<span data-ttu-id="a0d4b-123">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="a0d4b-123">Metadata Enumerations</span></span>](metadata-enumerations.md)
