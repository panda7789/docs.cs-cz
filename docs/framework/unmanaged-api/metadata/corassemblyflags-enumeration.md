---
title: CorAssemblyFlags – výčet
ms.date: 03/30/2017
api_name:
- CorAssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAssemblyFlags
helpviewer_keywords:
- CorAssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: bb8db3b6-d81d-49fc-b74c-dbc908a9eab9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 43bfec471fbcfc481e178f6610e0318e9538ee34
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025769"
---
# <a name="corassemblyflags-enumeration"></a><span data-ttu-id="b0b50-102">CorAssemblyFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="b0b50-102">CorAssemblyFlags Enumeration</span></span>
<span data-ttu-id="b0b50-103">Obsahuje hodnoty, které popisují metadata u sestavení.</span><span class="sxs-lookup"><span data-stu-id="b0b50-103">Contains values that describe the metadata applied to an assembly compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0b50-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0b50-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="b0b50-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b0b50-105">Members</span></span>  
  
|<span data-ttu-id="b0b50-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b0b50-106">Member</span></span>|<span data-ttu-id="b0b50-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b0b50-107">Description</span></span>|  
|------------|-----------------|  
|`afPublicKey`|<span data-ttu-id="b0b50-108">Označuje, že odkaz na sestavení obsahuje úplnou nezašifrované veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="b0b50-108">Indicates that the assembly reference holds the full, unhashed public key.</span></span>|  
|`afPA_None`|<span data-ttu-id="b0b50-109">Označuje, že neurčená na architektuře procesoru.</span><span class="sxs-lookup"><span data-stu-id="b0b50-109">Indicates that the processor architecture is unspecified.</span></span>|  
|`afPA_MSIL`|<span data-ttu-id="b0b50-110">Označuje, že je na architektuře procesoru neutrální (PE32).</span><span class="sxs-lookup"><span data-stu-id="b0b50-110">Indicates that the processor architecture is neutral (PE32).</span></span>|  
|`afPA_x86`|<span data-ttu-id="b0b50-111">Označuje, že je na architektuře procesoru x86 (PE32).</span><span class="sxs-lookup"><span data-stu-id="b0b50-111">Indicates that the processor architecture is x86 (PE32).</span></span>|  
|`afPA_IA64`|<span data-ttu-id="b0b50-112">Označuje, že je architektura procesorů Itanium (PE32 +).</span><span class="sxs-lookup"><span data-stu-id="b0b50-112">Indicates that the processor architecture is Itanium (PE32+).</span></span>|  
|`afPA_AMD64`|<span data-ttu-id="b0b50-113">Označuje, že je architektura procesorů AMD X64 (PE32 +).</span><span class="sxs-lookup"><span data-stu-id="b0b50-113">Indicates that the processor architecture is AMD X64 (PE32+).</span></span>|  
|`afPA_ARM`|<span data-ttu-id="b0b50-114">Označuje, že je na architektuře procesoru ARM (PE32).</span><span class="sxs-lookup"><span data-stu-id="b0b50-114">Indicates that the processor architecture is ARM (PE32).</span></span>|  
|`afPA_NoPlatform`|<span data-ttu-id="b0b50-115">Označuje, že sestavení je odkaz na sestavení; To znamená platí pro všechny architektury ale nelze je spustit na libovolné architektury.</span><span class="sxs-lookup"><span data-stu-id="b0b50-115">Indicates that the assembly is a reference assembly; that is, it applies to any architecture but cannot run on any architecture.</span></span> <span data-ttu-id="b0b50-116">Díky tomu se příznak je stejný jako `afPA_Mask`.</span><span class="sxs-lookup"><span data-stu-id="b0b50-116">Thus, the flag is the same as `afPA_Mask`.</span></span>|  
|`afPA_Specified`|<span data-ttu-id="b0b50-117">Označuje, že příznaky architektura procesoru by mělo být předáno `AssemblyRef` záznamu.</span><span class="sxs-lookup"><span data-stu-id="b0b50-117">Indicates that the processor architecture flags should be propagated to the `AssemblyRef` record.</span></span>|  
|`afPA_Mask`|<span data-ttu-id="b0b50-118">Maska, která popisuje architekturu procesoru.</span><span class="sxs-lookup"><span data-stu-id="b0b50-118">A mask that describes the processor architecture.</span></span>|  
|`afPA_FullMask`|<span data-ttu-id="b0b50-119">Určuje, že je součástí popis architektury procesoru.</span><span class="sxs-lookup"><span data-stu-id="b0b50-119">Specifies that the processor architecture description is included.</span></span>|  
|`afPA_Shift`|<span data-ttu-id="b0b50-120">Označuje počet posunů v příznacích architekturu procesoru, na a z indexu.</span><span class="sxs-lookup"><span data-stu-id="b0b50-120">Indicates a shift count in the processor architecture flags to and from the index.</span></span>|  
|`afEnableJITcompileTracking`|<span data-ttu-id="b0b50-121">Určuje odpovídající hodnotu z <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> z <xref:System.Diagnostics.DebuggableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b0b50-121">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afDisableJITcompileOptimizer`|<span data-ttu-id="b0b50-122">Určuje odpovídající hodnotu z <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> z <xref:System.Diagnostics.DebuggableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b0b50-122">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afRetargetable`|<span data-ttu-id="b0b50-123">Označuje, že sestavení můžete v době běhu změněn na cíl sestavení z jiného vydavatele.</span><span class="sxs-lookup"><span data-stu-id="b0b50-123">Indicates that the assembly can be retargeted at run time to an assembly from a different publisher.</span></span>|  
|`afContentType_Mask`|<span data-ttu-id="b0b50-124">Maska, která popisuje typ obsahu.</span><span class="sxs-lookup"><span data-stu-id="b0b50-124">A mask that describes the content type.</span></span>|  
|`afContentType_Default`|<span data-ttu-id="b0b50-125">Určuje výchozí typ obsahu.</span><span class="sxs-lookup"><span data-stu-id="b0b50-125">Indicates the default content type.</span></span>|  
|`afContentType_WindowsRuntime`|<span data-ttu-id="b0b50-126">Určuje typ obsahu modulu Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="b0b50-126">Indicates the Windows Runtime content type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b0b50-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b0b50-127">Requirements</span></span>  
 <span data-ttu-id="b0b50-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0b50-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0b50-129">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="b0b50-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b0b50-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0b50-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0b50-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b0b50-131">See also</span></span>

- [<span data-ttu-id="b0b50-132">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="b0b50-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
