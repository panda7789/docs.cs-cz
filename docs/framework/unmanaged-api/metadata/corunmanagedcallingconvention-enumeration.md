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
ms.openlocfilehash: 58d30e71929d314ee36adb9f83270858ff8a161b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442448"
---
# <a name="corunmanagedcallingconvention-enumeration"></a><span data-ttu-id="c4ec3-102">CorUnmanagedCallingConvention – výčet</span><span class="sxs-lookup"><span data-stu-id="c4ec3-102">CorUnmanagedCallingConvention Enumeration</span></span>
<span data-ttu-id="c4ec3-103">Specifies the calling conventions for unmanaged code.</span><span class="sxs-lookup"><span data-stu-id="c4ec3-103">Specifies the calling conventions for unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4ec3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4ec3-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="c4ec3-105">Členové</span><span class="sxs-lookup"><span data-stu-id="c4ec3-105">Members</span></span>  
  
|<span data-ttu-id="c4ec3-106">Člen</span><span class="sxs-lookup"><span data-stu-id="c4ec3-106">Member</span></span>|<span data-ttu-id="c4ec3-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c4ec3-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|<span data-ttu-id="c4ec3-108">The C language calling convention.</span><span class="sxs-lookup"><span data-stu-id="c4ec3-108">The C language calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|<span data-ttu-id="c4ec3-109">The standard calling convention.</span><span class="sxs-lookup"><span data-stu-id="c4ec3-109">The standard calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|<span data-ttu-id="c4ec3-110">The "this" calling convention.</span><span class="sxs-lookup"><span data-stu-id="c4ec3-110">The "this" calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|<span data-ttu-id="c4ec3-111">The "fast" calling convention.</span><span class="sxs-lookup"><span data-stu-id="c4ec3-111">The "fast" calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_C`|<span data-ttu-id="c4ec3-112">Not used.</span><span class="sxs-lookup"><span data-stu-id="c4ec3-112">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|<span data-ttu-id="c4ec3-113">Not used.</span><span class="sxs-lookup"><span data-stu-id="c4ec3-113">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|<span data-ttu-id="c4ec3-114">Not used.</span><span class="sxs-lookup"><span data-stu-id="c4ec3-114">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|<span data-ttu-id="c4ec3-115">Not used.</span><span class="sxs-lookup"><span data-stu-id="c4ec3-115">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4ec3-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4ec3-116">Remarks</span></span>  
 <span data-ttu-id="c4ec3-117">The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.</span><span class="sxs-lookup"><span data-stu-id="c4ec3-117">The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4ec3-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c4ec3-118">Requirements</span></span>  
 <span data-ttu-id="c4ec3-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4ec3-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4ec3-120">**Header:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="c4ec3-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="c4ec3-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4ec3-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4ec3-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4ec3-122">See also</span></span>

- [<span data-ttu-id="c4ec3-123">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="c4ec3-123">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
