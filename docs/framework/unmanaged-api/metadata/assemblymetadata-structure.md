---
title: "ASSEMBLYMETADATA – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ASSEMBLYMETADATA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ASSEMBLYMETADATA
helpviewer_keywords:
- ASSEMBLYMETADATA structure [.NET Framework metadata]
ms.assetid: 1af98e57-9145-4d35-bb78-77d1da7c91a5
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 819510c14bd67e7fcc739a19ea945f16b2a66c9a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="assemblymetadata-structure"></a><span data-ttu-id="2c1c2-102">ASSEMBLYMETADATA – struktura</span><span class="sxs-lookup"><span data-stu-id="2c1c2-102">ASSEMBLYMETADATA Structure</span></span>
<span data-ttu-id="2c1c2-103">Obsahuje informace o odkazované sestavení, včetně jeho verzi a jeho úrovně podpory pro národní prostředí, procesory a operační systémy.</span><span class="sxs-lookup"><span data-stu-id="2c1c2-103">Contains information about the referenced assembly, including its version and its level of support for locales, processors, and operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c1c2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c1c2-104">Syntax</span></span>  
  
```  
typedef struct {  
    USHORT  usMajorVersion;  
    USHORT  usMinorVersion;  
    USHORT  usBuildNumber;  
    USHORT  usRevisionNumber;  
    LPWSTR  szLocale;  
    ULONG   cbLocale;  
    DWORD*  rdwProcessor[];  
    ULONG   ulProcessor  
    OSINFO* rOS[];  
    ULONG   ulOS;  
} ASSEMBLYMETADATA;  
```  
  
## <a name="members"></a><span data-ttu-id="2c1c2-105">Členové</span><span class="sxs-lookup"><span data-stu-id="2c1c2-105">Members</span></span>  
  
|<span data-ttu-id="2c1c2-106">Člen</span><span class="sxs-lookup"><span data-stu-id="2c1c2-106">Member</span></span>|<span data-ttu-id="2c1c2-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2c1c2-107">Description</span></span>|  
|------------|-----------------|  
|`usMajorVersion`|<span data-ttu-id="2c1c2-108">Hlavní číslo verze odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="2c1c2-108">The major version number of the referenced assembly.</span></span> <span data-ttu-id="2c1c2-109">Tato hodnota nemůže být nula.</span><span class="sxs-lookup"><span data-stu-id="2c1c2-109">This value cannot be zero.</span></span> <span data-ttu-id="2c1c2-110">Pokud všechny bity `usMajorVersion` jsou nastavené, není zadán hlavní verzi.</span><span class="sxs-lookup"><span data-stu-id="2c1c2-110">If all the bits of `usMajorVersion` are set, the major version is not specified.</span></span>|  
|`usMinorVersion`|<span data-ttu-id="2c1c2-111">Číslo podverze odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="2c1c2-111">The minor version number of the referenced assembly.</span></span> <span data-ttu-id="2c1c2-112">Tato hodnota nemůže být nula.</span><span class="sxs-lookup"><span data-stu-id="2c1c2-112">This value cannot be zero.</span></span> <span data-ttu-id="2c1c2-113">Pokud všechny bity `usMinorVersion` jsou nastavené na podverzi není zadán.</span><span class="sxs-lookup"><span data-stu-id="2c1c2-113">If all the bits of `usMinorVersion` are set, the minor version is not specified.</span></span>|  
|`usBuildNumber`|<span data-ttu-id="2c1c2-114">Číslo sestavení odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="2c1c2-114">The build number of the referenced assembly.</span></span> <span data-ttu-id="2c1c2-115">Tato hodnota nemůže být nula.</span><span class="sxs-lookup"><span data-stu-id="2c1c2-115">This value cannot be zero.</span></span> <span data-ttu-id="2c1c2-116">Pokud všechny bity `usBuildNumber` jsou nastavené, číslo sestavení není zadán.</span><span class="sxs-lookup"><span data-stu-id="2c1c2-116">If all the bits of `usBuildNumber` are set, the build number is not specified.</span></span>|  
|`usRevisionNumber`|<span data-ttu-id="2c1c2-117">Číslo revize odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="2c1c2-117">The revision number of the referenced assembly.</span></span> <span data-ttu-id="2c1c2-118">Tato hodnota nemůže být nula.</span><span class="sxs-lookup"><span data-stu-id="2c1c2-118">This value cannot be zero.</span></span> <span data-ttu-id="2c1c2-119">Pokud všechny bity `usRevisionNumber` jsou nastavené, číslo revize není zadán.</span><span class="sxs-lookup"><span data-stu-id="2c1c2-119">If all the bits of `usRevisionNumber` are set, the revision number is not specified.</span></span>|  
|`szLocale`|<span data-ttu-id="2c1c2-120">Seznam názvů národní prostředí podle specifikace RFC1766, oddělené středníky, zadání národní prostředí nepodporuje odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="2c1c2-120">A list of locale names conforming to the RFC1766 specification, separated by semicolons, specifying the locales supported by the referenced assembly.</span></span> <span data-ttu-id="2c1c2-121">Hodnota null určuje nezávislost národního prostředí.</span><span class="sxs-lookup"><span data-stu-id="2c1c2-121">A null value indicates locale independence.</span></span> <span data-ttu-id="2c1c2-122">**Poznámka:** v rozhraní .NET Framework verze 1.0 nelze zadat více než jeden národního prostředí.</span><span class="sxs-lookup"><span data-stu-id="2c1c2-122">**Note:**  In the .NET Framework version 1.0 you cannot specify more than one locale.</span></span>|  
|`cbLocale`|<span data-ttu-id="2c1c2-123">Velikost v široké znaky `szLocale`.</span><span class="sxs-lookup"><span data-stu-id="2c1c2-123">The size in wide characters of `szLocale`.</span></span>|  
|`rdwProcessor`|<span data-ttu-id="2c1c2-124">Pole identifikátory, jak jsou definovány v souboru Winnt.h, pro typy procesoru, které jsou podporovány odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="2c1c2-124">An array of identifiers, as defined in Winnt.h, for the processor types that are supported by the referenced assembly.</span></span> <span data-ttu-id="2c1c2-125">Hodnota NULL určuje nezávislost procesoru.</span><span class="sxs-lookup"><span data-stu-id="2c1c2-125">A NULL value indicates processor independence.</span></span>|  
|`ulProcessor`|<span data-ttu-id="2c1c2-126">Délka `rdwProcessor` pole.</span><span class="sxs-lookup"><span data-stu-id="2c1c2-126">The length of the `rdwProcessor` array.</span></span>|  
|`rOS`|<span data-ttu-id="2c1c2-127">Pole [osinfo –](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) instance zadání operační systémy, které jsou podporovány odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="2c1c2-127">An array of [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) instances specifying the operating systems that are supported by the referenced assembly.</span></span> <span data-ttu-id="2c1c2-128">Hodnota NULL znamená nezávislost operačního systému.</span><span class="sxs-lookup"><span data-stu-id="2c1c2-128">A NULL value indicates operating-system independence.</span></span>|  
|`ulOS`|<span data-ttu-id="2c1c2-129">Délka `rOS` pole.</span><span class="sxs-lookup"><span data-stu-id="2c1c2-129">The length of the `rOS` array.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2c1c2-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2c1c2-130">Requirements</span></span>  
 <span data-ttu-id="2c1c2-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c1c2-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c1c2-132">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2c1c2-132">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2c1c2-133">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2c1c2-133">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2c1c2-134">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c1c2-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c1c2-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="2c1c2-135">See Also</span></span>  
 [<span data-ttu-id="2c1c2-136">Struktury pro metadata</span><span class="sxs-lookup"><span data-stu-id="2c1c2-136">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [<span data-ttu-id="2c1c2-137">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2c1c2-137">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="2c1c2-138">OSINFO – struktura</span><span class="sxs-lookup"><span data-stu-id="2c1c2-138">OSINFO Structure</span></span>](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)
