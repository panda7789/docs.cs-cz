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
ms.openlocfilehash: eca4b66a3f7c1a96bb06827dde477f34cb904ba3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61906240"
---
# <a name="corassemblyflags-enumeration"></a><span data-ttu-id="f2114-102">CorAssemblyFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="f2114-102">CorAssemblyFlags Enumeration</span></span>
<span data-ttu-id="f2114-103">Obsahuje hodnoty, které popisují metadata u sestavení.</span><span class="sxs-lookup"><span data-stu-id="f2114-103">Contains values that describe the metadata applied to an assembly compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2114-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2114-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="f2114-105">Členové</span><span class="sxs-lookup"><span data-stu-id="f2114-105">Members</span></span>  
  
|<span data-ttu-id="f2114-106">Člen</span><span class="sxs-lookup"><span data-stu-id="f2114-106">Member</span></span>|<span data-ttu-id="f2114-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f2114-107">Description</span></span>|  
|------------|-----------------|  
|`afPublicKey`|<span data-ttu-id="f2114-108">Označuje, že odkaz na sestavení obsahuje úplnou nezašifrované veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="f2114-108">Indicates that the assembly reference holds the full, unhashed public key.</span></span>|  
|`afPA_None`|<span data-ttu-id="f2114-109">Označuje, že neurčená na architektuře procesoru.</span><span class="sxs-lookup"><span data-stu-id="f2114-109">Indicates that the processor architecture is unspecified.</span></span>|  
|`afPA_MSIL`|<span data-ttu-id="f2114-110">Označuje, že je na architektuře procesoru neutrální (PE32).</span><span class="sxs-lookup"><span data-stu-id="f2114-110">Indicates that the processor architecture is neutral (PE32).</span></span>|  
|`afPA_x86`|<span data-ttu-id="f2114-111">Označuje, že je na architektuře procesoru x86 (PE32).</span><span class="sxs-lookup"><span data-stu-id="f2114-111">Indicates that the processor architecture is x86 (PE32).</span></span>|  
|`afPA_IA64`|<span data-ttu-id="f2114-112">Označuje, že je architektura procesorů Itanium (PE32 +).</span><span class="sxs-lookup"><span data-stu-id="f2114-112">Indicates that the processor architecture is Itanium (PE32+).</span></span>|  
|`afPA_AMD64`|<span data-ttu-id="f2114-113">Označuje, že je architektura procesorů AMD X64 (PE32 +).</span><span class="sxs-lookup"><span data-stu-id="f2114-113">Indicates that the processor architecture is AMD X64 (PE32+).</span></span>|  
|`afPA_ARM`|<span data-ttu-id="f2114-114">Označuje, že je na architektuře procesoru ARM (PE32).</span><span class="sxs-lookup"><span data-stu-id="f2114-114">Indicates that the processor architecture is ARM (PE32).</span></span>|  
|`afPA_NoPlatform`|<span data-ttu-id="f2114-115">Označuje, že sestavení je odkaz na sestavení; To znamená platí pro všechny architektury ale nelze je spustit na libovolné architektury.</span><span class="sxs-lookup"><span data-stu-id="f2114-115">Indicates that the assembly is a reference assembly; that is, it applies to any architecture but cannot run on any architecture.</span></span> <span data-ttu-id="f2114-116">Díky tomu se příznak je stejný jako `afPA_Mask`.</span><span class="sxs-lookup"><span data-stu-id="f2114-116">Thus, the flag is the same as `afPA_Mask`.</span></span>|  
|`afPA_Specified`|<span data-ttu-id="f2114-117">Označuje, že příznaky architektura procesoru by mělo být předáno `AssemblyRef` záznamu.</span><span class="sxs-lookup"><span data-stu-id="f2114-117">Indicates that the processor architecture flags should be propagated to the `AssemblyRef` record.</span></span>|  
|`afPA_Mask`|<span data-ttu-id="f2114-118">Maska, která popisuje architekturu procesoru.</span><span class="sxs-lookup"><span data-stu-id="f2114-118">A mask that describes the processor architecture.</span></span>|  
|`afPA_FullMask`|<span data-ttu-id="f2114-119">Určuje, že je součástí popis architektury procesoru.</span><span class="sxs-lookup"><span data-stu-id="f2114-119">Specifies that the processor architecture description is included.</span></span>|  
|`afPA_Shift`|<span data-ttu-id="f2114-120">Označuje počet posunů v příznacích architekturu procesoru, na a z indexu.</span><span class="sxs-lookup"><span data-stu-id="f2114-120">Indicates a shift count in the processor architecture flags to and from the index.</span></span>|  
|`afEnableJITcompileTracking`|<span data-ttu-id="f2114-121">Určuje odpovídající hodnotu z <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> z <xref:System.Diagnostics.DebuggableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f2114-121">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afDisableJITcompileOptimizer`|<span data-ttu-id="f2114-122">Určuje odpovídající hodnotu z <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> z <xref:System.Diagnostics.DebuggableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f2114-122">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afRetargetable`|<span data-ttu-id="f2114-123">Označuje, že sestavení můžete v době běhu změněn na cíl sestavení z jiného vydavatele.</span><span class="sxs-lookup"><span data-stu-id="f2114-123">Indicates that the assembly can be retargeted at run time to an assembly from a different publisher.</span></span>|  
|`afContentType_Mask`|<span data-ttu-id="f2114-124">Maska, která popisuje typ obsahu.</span><span class="sxs-lookup"><span data-stu-id="f2114-124">A mask that describes the content type.</span></span>|  
|`afContentType_Default`|<span data-ttu-id="f2114-125">Určuje výchozí typ obsahu.</span><span class="sxs-lookup"><span data-stu-id="f2114-125">Indicates the default content type.</span></span>|  
|`afContentType_WindowsRuntime`|<span data-ttu-id="f2114-126">Označuje, [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typ obsahu.</span><span class="sxs-lookup"><span data-stu-id="f2114-126">Indicates the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] content type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f2114-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f2114-127">Requirements</span></span>  
 <span data-ttu-id="f2114-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2114-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2114-129">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="f2114-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="f2114-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2114-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2114-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2114-131">See also</span></span>

- [<span data-ttu-id="f2114-132">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="f2114-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
