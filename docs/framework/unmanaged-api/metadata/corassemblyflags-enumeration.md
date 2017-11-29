---
title: "CorAssemblyFlags – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorAssemblyFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: CorAssemblyFlags
helpviewer_keywords: CorAssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: bb8db3b6-d81d-49fc-b74c-dbc908a9eab9
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 67057944705a1cecd1754c3c11da08725c9a93f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="corassemblyflags-enumeration"></a><span data-ttu-id="9ae91-102">CorAssemblyFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="9ae91-102">CorAssemblyFlags Enumeration</span></span>
<span data-ttu-id="9ae91-103">Obsahuje hodnoty, které popisují metadata použít sestavení kompilace.</span><span class="sxs-lookup"><span data-stu-id="9ae91-103">Contains values that describe the metadata applied to an assembly compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ae91-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ae91-104">Syntax</span></span>  
  
```  
typedef enum CorAssemblyFlags {  
  
    afPublicKey             =   0x0001,  
    afPA_None               =   0x0000,  
    afPA_MSIL               =   0x0010,  
    afPA_x86                =   0x0020,  
    afPA_IA64               =   0x0030,  
    afPA_AMD64              =   0x0040,  
    afPA_ARM                =   0x0050,  
    afPA_NoPlatform         =   0x0070,  
    afPA_Specified          =   0x0080,  
    afPA_Mask               =   0x0070,  
    afPA_FullMask           =   0x00F0,  
    afPA_Shift              =   0x0004,  
  
    afEnableJITcompileTracking  =   0x8000,  
    afDisableJITcompileOptimizer=   0x4000,  
  
    afRetargetable          =   0x0100,  
    afContentType_Default        =   0x0000,  
    afContentType_WindowsRuntime =   0x0200,  
    afContentType_Mask           =   0x0E00,  
  
} CorAssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="9ae91-105">Členové</span><span class="sxs-lookup"><span data-stu-id="9ae91-105">Members</span></span>  
  
|<span data-ttu-id="9ae91-106">Člen</span><span class="sxs-lookup"><span data-stu-id="9ae91-106">Member</span></span>|<span data-ttu-id="9ae91-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9ae91-107">Description</span></span>|  
|------------|-----------------|  
|`afPublicKey`|<span data-ttu-id="9ae91-108">Označuje, že odkaz na sestavení obsahuje veřejný klíč, úplné a bez otisku.</span><span class="sxs-lookup"><span data-stu-id="9ae91-108">Indicates that the assembly reference holds the full, unhashed public key.</span></span>|  
|`afPA_None`|<span data-ttu-id="9ae91-109">Označuje, že neurčené na architektuře procesoru.</span><span class="sxs-lookup"><span data-stu-id="9ae91-109">Indicates that the processor architecture is unspecified.</span></span>|  
|`afPA_MSIL`|<span data-ttu-id="9ae91-110">Označuje, že je na architektuře procesoru neutrální (PE32).</span><span class="sxs-lookup"><span data-stu-id="9ae91-110">Indicates that the processor architecture is neutral (PE32).</span></span>|  
|`afPA_x86`|<span data-ttu-id="9ae91-111">Označuje, že je na architektuře procesoru x86 (PE32).</span><span class="sxs-lookup"><span data-stu-id="9ae91-111">Indicates that the processor architecture is x86 (PE32).</span></span>|  
|`afPA_IA64`|<span data-ttu-id="9ae91-112">Označuje, že je na architektuře procesoru pro procesory Itanium (PE32 +).</span><span class="sxs-lookup"><span data-stu-id="9ae91-112">Indicates that the processor architecture is Itanium (PE32+).</span></span>|  
|`afPA_AMD64`|<span data-ttu-id="9ae91-113">Označuje, že je na architektuře procesoru AMD X64 (PE32 +).</span><span class="sxs-lookup"><span data-stu-id="9ae91-113">Indicates that the processor architecture is AMD X64 (PE32+).</span></span>|  
|`afPA_ARM`|<span data-ttu-id="9ae91-114">Označuje, že je na architektuře procesoru ARM (PE32).</span><span class="sxs-lookup"><span data-stu-id="9ae91-114">Indicates that the processor architecture is ARM (PE32).</span></span>|  
|`afPA_NoPlatform`|<span data-ttu-id="9ae91-115">Označuje, že je sestavení referenční sestavení při; To znamená platí pro všechny architektura však nelze spustit na jakékoli architektuře.</span><span class="sxs-lookup"><span data-stu-id="9ae91-115">Indicates that the assembly is a reference assembly; that is, it applies to any architecture but cannot run on any architecture.</span></span> <span data-ttu-id="9ae91-116">Proto příznak je stejný jako `afPA_Mask`.</span><span class="sxs-lookup"><span data-stu-id="9ae91-116">Thus, the flag is the same as `afPA_Mask`.</span></span>|  
|`afPA_Specified`|<span data-ttu-id="9ae91-117">Označuje, že příznaky architektura procesoru by mělo být předáno `AssemblyRef` záznamu.</span><span class="sxs-lookup"><span data-stu-id="9ae91-117">Indicates that the processor architecture flags should be propagated to the `AssemblyRef` record.</span></span>|  
|`afPA_Mask`|<span data-ttu-id="9ae91-118">Maska, která popisuje architekturu procesoru.</span><span class="sxs-lookup"><span data-stu-id="9ae91-118">A mask that describes the processor architecture.</span></span>|  
|`afPA_FullMask`|<span data-ttu-id="9ae91-119">Určuje, že je zahrnuté popis architekturu procesoru.</span><span class="sxs-lookup"><span data-stu-id="9ae91-119">Specifies that the processor architecture description is included.</span></span>|  
|`afPA_Shift`|<span data-ttu-id="9ae91-120">Určuje počet posunutí v příznaky architektura procesoru do a z indexu.</span><span class="sxs-lookup"><span data-stu-id="9ae91-120">Indicates a shift count in the processor architecture flags to and from the index.</span></span>|  
|`afEnableJITcompileTracking`|<span data-ttu-id="9ae91-121">Určuje odpovídající hodnotu z <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> z <xref:System.Diagnostics.DebuggableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9ae91-121">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afDisableJITcompileOptimizer`|<span data-ttu-id="9ae91-122">Určuje odpovídající hodnotu z <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> z <xref:System.Diagnostics.DebuggableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9ae91-122">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afRetargetable`|<span data-ttu-id="9ae91-123">Označuje, že sestavení může být v době běhu změnit cíl na necílené sestavení z jiného vydavatele.</span><span class="sxs-lookup"><span data-stu-id="9ae91-123">Indicates that the assembly can be retargeted at run time to an assembly from a different publisher.</span></span>|  
|`afContentType_Mask`|<span data-ttu-id="9ae91-124">Maska, která popisuje typ obsahu.</span><span class="sxs-lookup"><span data-stu-id="9ae91-124">A mask that describes the content type.</span></span>|  
|`afContentType_Default`|<span data-ttu-id="9ae91-125">Určuje výchozí typ obsahu.</span><span class="sxs-lookup"><span data-stu-id="9ae91-125">Indicates the default content type.</span></span>|  
|`afContentType_WindowsRuntime`|<span data-ttu-id="9ae91-126">Určuje, [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typ obsahu.</span><span class="sxs-lookup"><span data-stu-id="9ae91-126">Indicates the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] content type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9ae91-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9ae91-127">Requirements</span></span>  
 <span data-ttu-id="9ae91-128">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ae91-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ae91-129">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="9ae91-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="9ae91-130">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ae91-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ae91-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="9ae91-131">See Also</span></span>  
 [<span data-ttu-id="9ae91-132">Výčty metadat</span><span class="sxs-lookup"><span data-stu-id="9ae91-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
