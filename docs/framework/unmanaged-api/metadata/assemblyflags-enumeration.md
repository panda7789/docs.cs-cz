---
title: AssemblyFlags – výčet
ms.date: 03/30/2017
api_name:
- AssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyFlags
helpviewer_keywords:
- AssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: 40f9bd9e-16ec-447e-81b0-168c875e9866
topic_type:
- apiref
ms.openlocfilehash: 1cb84b94b37a2e9e8dd4d20d09cbca82db290c0f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009445"
---
# <a name="assemblyflags-enumeration"></a><span data-ttu-id="f8130-102">AssemblyFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="f8130-102">AssemblyFlags Enumeration</span></span>
<span data-ttu-id="f8130-103">Obsahuje hodnoty, které popisují funkce běhu sestavení.</span><span class="sxs-lookup"><span data-stu-id="f8130-103">Contains values that describe run-time features of an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8130-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8130-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="f8130-105">Členové</span><span class="sxs-lookup"><span data-stu-id="f8130-105">Members</span></span>  
  
|<span data-ttu-id="f8130-106">Člen</span><span class="sxs-lookup"><span data-stu-id="f8130-106">Member</span></span>|<span data-ttu-id="f8130-107">Description</span><span class="sxs-lookup"><span data-stu-id="f8130-107">Description</span></span>|  
|------------|-----------------|  
|`afImplicitExportedTypes`|<span data-ttu-id="f8130-108">Určuje, že exportované definice typu jsou implicitní v rámci souborů, které tvoří sestavení.</span><span class="sxs-lookup"><span data-stu-id="f8130-108">Specifies that exported type definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="f8130-109">V .NET Framework verzích 1,0 a 1,1 je tato hodnota vždycky nastavená.</span><span class="sxs-lookup"><span data-stu-id="f8130-109">In the .NET Framework versions 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afImplicitResources`|<span data-ttu-id="f8130-110">Určuje, že definice prostředků jsou implicitní v rámci souborů, které tvoří sestavení.</span><span class="sxs-lookup"><span data-stu-id="f8130-110">Specifies that resource definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="f8130-111">V .NET Framework 1,0 a 1,1 je tato hodnota vždy nastavena jako nastavená.</span><span class="sxs-lookup"><span data-stu-id="f8130-111">In the .NET Framework 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afNonSideBySideAppDomain`|<span data-ttu-id="f8130-112">Určuje, že sestavení nemůže být spuštěno s jinými verzemi, pokud jsou spuštěny ve stejné doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="f8130-112">Specifies that the assembly cannot execute with other versions if they are running in the same application domain.</span></span>|  
|`afNonSideBySideProcess`|<span data-ttu-id="f8130-113">Určuje, že sestavení nemůže být spuštěno s jinými verzemi, pokud jsou spuštěny ve stejném procesu.</span><span class="sxs-lookup"><span data-stu-id="f8130-113">Specifies that the assembly cannot execute with other versions if they are running in the same process.</span></span>|  
|`afNonSideBySideMachine`|<span data-ttu-id="f8130-114">Určuje, že sestavení nemůže být spuštěno s jinými verzemi, pokud jsou spuštěny ve stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="f8130-114">Specifies that the assembly cannot execute with other versions if they are running on the same computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8130-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f8130-115">Remarks</span></span>  
 <span data-ttu-id="f8130-116">Hodnoty mezi 0x0010 a 0x0070, včetně, se používají k popisu souběžných funkcí kompatibility odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="f8130-116">The values between 0x0010 and 0x0070, inclusive, are used to describe side-by-side compatibility features of the referenced assembly.</span></span> <span data-ttu-id="f8130-117">Pokud žádná z těchto hodnot není nastavena, předpokládá se, že sestavení je souběžně kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="f8130-117">If none of these values are set, the assembly is assumed to be side-by-side compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8130-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f8130-118">Requirements</span></span>  
 <span data-ttu-id="f8130-119">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8130-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8130-120">**Hlavička:** MsCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f8130-120">**Header:** MsCorEE.h</span></span>  
  
 <span data-ttu-id="f8130-121">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f8130-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f8130-122">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8130-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8130-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="f8130-123">See also</span></span>

- [<span data-ttu-id="f8130-124">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="f8130-124">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="f8130-125">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f8130-125">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
