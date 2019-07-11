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
ms.openlocfilehash: 9206fbde13f457d4b2e2941ee744d645c6df9774
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782000"
---
# <a name="corunmanagedcallingconvention-enumeration"></a><span data-ttu-id="f5c2e-102">CorUnmanagedCallingConvention – výčet</span><span class="sxs-lookup"><span data-stu-id="f5c2e-102">CorUnmanagedCallingConvention Enumeration</span></span>
<span data-ttu-id="f5c2e-103">Určuje konvence volání nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="f5c2e-103">Specifies the calling conventions for unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5c2e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5c2e-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="f5c2e-105">Členové</span><span class="sxs-lookup"><span data-stu-id="f5c2e-105">Members</span></span>  
  
|<span data-ttu-id="f5c2e-106">Člen</span><span class="sxs-lookup"><span data-stu-id="f5c2e-106">Member</span></span>|<span data-ttu-id="f5c2e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f5c2e-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|<span data-ttu-id="f5c2e-108">C jazykové konvence volání.</span><span class="sxs-lookup"><span data-stu-id="f5c2e-108">The C language calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|<span data-ttu-id="f5c2e-109">Standardní konvence volání.</span><span class="sxs-lookup"><span data-stu-id="f5c2e-109">The standard calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|<span data-ttu-id="f5c2e-110">"Tento" konvence volání.</span><span class="sxs-lookup"><span data-stu-id="f5c2e-110">The "this" calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|<span data-ttu-id="f5c2e-111">"Rychlé" konvence volání.</span><span class="sxs-lookup"><span data-stu-id="f5c2e-111">The "fast" calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_C`|<span data-ttu-id="f5c2e-112">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="f5c2e-112">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|<span data-ttu-id="f5c2e-113">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="f5c2e-113">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|<span data-ttu-id="f5c2e-114">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="f5c2e-114">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|<span data-ttu-id="f5c2e-115">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="f5c2e-115">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5c2e-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f5c2e-116">Remarks</span></span>  
 <span data-ttu-id="f5c2e-117">Modul CLR nepodporuje "rychlé" konvence volání v rozhraní .NET Framework verze 1.0.</span><span class="sxs-lookup"><span data-stu-id="f5c2e-117">The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5c2e-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f5c2e-118">Requirements</span></span>  
 <span data-ttu-id="f5c2e-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5c2e-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5c2e-120">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="f5c2e-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="f5c2e-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5c2e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5c2e-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f5c2e-122">See also</span></span>

- [<span data-ttu-id="f5c2e-123">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="f5c2e-123">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
