---
title: ASSEMBLYMETADATA – struktura
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f0a9b9c149c86b4d9121275aa858dfdc0cdbac7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59195160"
---
# <a name="assemblymetadata-structure"></a><span data-ttu-id="421c1-102">ASSEMBLYMETADATA – struktura</span><span class="sxs-lookup"><span data-stu-id="421c1-102">ASSEMBLYMETADATA Structure</span></span>
<span data-ttu-id="421c1-103">Obsahuje informace o odkazovaném sestavení, včetně jeho verze a jeho úroveň podpory pro národní prostředí, procesory a operační systémy.</span><span class="sxs-lookup"><span data-stu-id="421c1-103">Contains information about the referenced assembly, including its version and its level of support for locales, processors, and operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="421c1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="421c1-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="421c1-105">Členové</span><span class="sxs-lookup"><span data-stu-id="421c1-105">Members</span></span>  
  
|<span data-ttu-id="421c1-106">Člen</span><span class="sxs-lookup"><span data-stu-id="421c1-106">Member</span></span>|<span data-ttu-id="421c1-107">Popis</span><span class="sxs-lookup"><span data-stu-id="421c1-107">Description</span></span>|  
|------------|-----------------|  
|`usMajorVersion`|<span data-ttu-id="421c1-108">Číslo hlavní verze odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="421c1-108">The major version number of the referenced assembly.</span></span> <span data-ttu-id="421c1-109">Tato hodnota nemůže být nula.</span><span class="sxs-lookup"><span data-stu-id="421c1-109">This value cannot be zero.</span></span> <span data-ttu-id="421c1-110">Pokud všechny bity `usMajorVersion` je nastaveno, hlavní verze není zadán.</span><span class="sxs-lookup"><span data-stu-id="421c1-110">If all the bits of `usMajorVersion` are set, the major version is not specified.</span></span>|  
|`usMinorVersion`|<span data-ttu-id="421c1-111">Číslo podverze odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="421c1-111">The minor version number of the referenced assembly.</span></span> <span data-ttu-id="421c1-112">Tato hodnota nemůže být nula.</span><span class="sxs-lookup"><span data-stu-id="421c1-112">This value cannot be zero.</span></span> <span data-ttu-id="421c1-113">Pokud všechny bity `usMinorVersion` je nastaveno, vedlejší verze není zadán.</span><span class="sxs-lookup"><span data-stu-id="421c1-113">If all the bits of `usMinorVersion` are set, the minor version is not specified.</span></span>|  
|`usBuildNumber`|<span data-ttu-id="421c1-114">Číslo sestavení odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="421c1-114">The build number of the referenced assembly.</span></span> <span data-ttu-id="421c1-115">Tato hodnota nemůže být nula.</span><span class="sxs-lookup"><span data-stu-id="421c1-115">This value cannot be zero.</span></span> <span data-ttu-id="421c1-116">Pokud všechny bity `usBuildNumber` je nastaveno, není určeno číslo sestavení.</span><span class="sxs-lookup"><span data-stu-id="421c1-116">If all the bits of `usBuildNumber` are set, the build number is not specified.</span></span>|  
|`usRevisionNumber`|<span data-ttu-id="421c1-117">Číslo revize odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="421c1-117">The revision number of the referenced assembly.</span></span> <span data-ttu-id="421c1-118">Tato hodnota nemůže být nula.</span><span class="sxs-lookup"><span data-stu-id="421c1-118">This value cannot be zero.</span></span> <span data-ttu-id="421c1-119">Pokud všechny bity `usRevisionNumber` je nastaveno, není určeno číslo revize.</span><span class="sxs-lookup"><span data-stu-id="421c1-119">If all the bits of `usRevisionNumber` are set, the revision number is not specified.</span></span>|  
|`szLocale`|<span data-ttu-id="421c1-120">Seznam názvů národních prostředí, který odpovídá specifikaci RFC1766 oddělené středníkem, určení národních prostředí podporovaných odkazovaných sestavení.</span><span class="sxs-lookup"><span data-stu-id="421c1-120">A list of locale names conforming to the RFC1766 specification, separated by semicolons, specifying the locales supported by the referenced assembly.</span></span> <span data-ttu-id="421c1-121">Hodnota null znamená nezávislost národní prostředí.</span><span class="sxs-lookup"><span data-stu-id="421c1-121">A null value indicates locale independence.</span></span> <span data-ttu-id="421c1-122">**Poznámka:**  V rozhraní .NET Framework verze 1.0 nelze zadat více než jedno prostředí.</span><span class="sxs-lookup"><span data-stu-id="421c1-122">**Note:**  In the .NET Framework version 1.0 you cannot specify more than one locale.</span></span>|  
|`cbLocale`|<span data-ttu-id="421c1-123">Velikost v širokých znaků `szLocale`.</span><span class="sxs-lookup"><span data-stu-id="421c1-123">The size in wide characters of `szLocale`.</span></span>|  
|`rdwProcessor`|<span data-ttu-id="421c1-124">Pole identifikátory, jak jsou definovány v souboru Winnt.h, pro typy procesorů, které jsou podporovány odkazovaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="421c1-124">An array of identifiers, as defined in Winnt.h, for the processor types that are supported by the referenced assembly.</span></span> <span data-ttu-id="421c1-125">Hodnota NULL znamená nezávislost procesoru.</span><span class="sxs-lookup"><span data-stu-id="421c1-125">A NULL value indicates processor independence.</span></span>|  
|`ulProcessor`|<span data-ttu-id="421c1-126">Délka `rdwProcessor` pole.</span><span class="sxs-lookup"><span data-stu-id="421c1-126">The length of the `rdwProcessor` array.</span></span>|  
|`rOS`|<span data-ttu-id="421c1-127">Pole [osinfo –](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) instance zadání operační systémy, které jsou podporovány odkazovaném sestavení.</span><span class="sxs-lookup"><span data-stu-id="421c1-127">An array of [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) instances specifying the operating systems that are supported by the referenced assembly.</span></span> <span data-ttu-id="421c1-128">Hodnota NULL znamená nezávislost operačního systému.</span><span class="sxs-lookup"><span data-stu-id="421c1-128">A NULL value indicates operating-system independence.</span></span>|  
|`ulOS`|<span data-ttu-id="421c1-129">Délka `rOS` pole.</span><span class="sxs-lookup"><span data-stu-id="421c1-129">The length of the `rOS` array.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="421c1-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="421c1-130">Requirements</span></span>  
 <span data-ttu-id="421c1-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="421c1-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="421c1-132">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="421c1-132">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="421c1-133">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="421c1-133">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="421c1-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="421c1-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="421c1-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="421c1-135">See also</span></span>

- [<span data-ttu-id="421c1-136">Struktury pro metadata</span><span class="sxs-lookup"><span data-stu-id="421c1-136">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="421c1-137">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="421c1-137">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="421c1-138">OSINFO – struktura</span><span class="sxs-lookup"><span data-stu-id="421c1-138">OSINFO Structure</span></span>](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)
