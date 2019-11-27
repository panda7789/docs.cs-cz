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
ms.openlocfilehash: 24ec1f7d553a59425f7eb02af8e91010d940eb07
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444265"
---
# <a name="assemblymetadata-structure"></a><span data-ttu-id="50922-102">ASSEMBLYMETADATA – struktura</span><span class="sxs-lookup"><span data-stu-id="50922-102">ASSEMBLYMETADATA Structure</span></span>
<span data-ttu-id="50922-103">Obsahuje informace o odkazovaném sestavení, včetně jeho verze a jeho úrovně podpory pro národní prostředí, procesory a operační systémy.</span><span class="sxs-lookup"><span data-stu-id="50922-103">Contains information about the referenced assembly, including its version and its level of support for locales, processors, and operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50922-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50922-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="50922-105">Členové</span><span class="sxs-lookup"><span data-stu-id="50922-105">Members</span></span>  
  
|<span data-ttu-id="50922-106">Člen</span><span class="sxs-lookup"><span data-stu-id="50922-106">Member</span></span>|<span data-ttu-id="50922-107">Popis</span><span class="sxs-lookup"><span data-stu-id="50922-107">Description</span></span>|  
|------------|-----------------|  
|`usMajorVersion`|<span data-ttu-id="50922-108">Hlavní číslo verze odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="50922-108">The major version number of the referenced assembly.</span></span> <span data-ttu-id="50922-109">Tato hodnota nemůže být nulová.</span><span class="sxs-lookup"><span data-stu-id="50922-109">This value cannot be zero.</span></span> <span data-ttu-id="50922-110">Pokud jsou nastaveny všechny bity `usMajorVersion`, není určena hlavní verze.</span><span class="sxs-lookup"><span data-stu-id="50922-110">If all the bits of `usMajorVersion` are set, the major version is not specified.</span></span>|  
|`usMinorVersion`|<span data-ttu-id="50922-111">Číslo dílčí verze odkazovaného sestavení</span><span class="sxs-lookup"><span data-stu-id="50922-111">The minor version number of the referenced assembly.</span></span> <span data-ttu-id="50922-112">Tato hodnota nemůže být nulová.</span><span class="sxs-lookup"><span data-stu-id="50922-112">This value cannot be zero.</span></span> <span data-ttu-id="50922-113">Pokud jsou nastaveny všechny bity `usMinorVersion`, není určena vedlejší verze.</span><span class="sxs-lookup"><span data-stu-id="50922-113">If all the bits of `usMinorVersion` are set, the minor version is not specified.</span></span>|  
|`usBuildNumber`|<span data-ttu-id="50922-114">Číslo sestavení odkazovaného sestavení</span><span class="sxs-lookup"><span data-stu-id="50922-114">The build number of the referenced assembly.</span></span> <span data-ttu-id="50922-115">Tato hodnota nemůže být nulová.</span><span class="sxs-lookup"><span data-stu-id="50922-115">This value cannot be zero.</span></span> <span data-ttu-id="50922-116">Pokud jsou nastaveny všechny bity `usBuildNumber`, číslo sestavení není zadáno.</span><span class="sxs-lookup"><span data-stu-id="50922-116">If all the bits of `usBuildNumber` are set, the build number is not specified.</span></span>|  
|`usRevisionNumber`|<span data-ttu-id="50922-117">Číslo revize odkazovaného sestavení</span><span class="sxs-lookup"><span data-stu-id="50922-117">The revision number of the referenced assembly.</span></span> <span data-ttu-id="50922-118">Tato hodnota nemůže být nulová.</span><span class="sxs-lookup"><span data-stu-id="50922-118">This value cannot be zero.</span></span> <span data-ttu-id="50922-119">Pokud jsou nastaveny všechny bity `usRevisionNumber`, číslo revize není zadáno.</span><span class="sxs-lookup"><span data-stu-id="50922-119">If all the bits of `usRevisionNumber` are set, the revision number is not specified.</span></span>|  
|`szLocale`|<span data-ttu-id="50922-120">Seznam názvů národních prostředí, které odpovídají specifikaci RFC1766, oddělený středníky a určením národních prostředí podporovaných odkazovaným sestavením.</span><span class="sxs-lookup"><span data-stu-id="50922-120">A list of locale names conforming to the RFC1766 specification, separated by semicolons, specifying the locales supported by the referenced assembly.</span></span> <span data-ttu-id="50922-121">Hodnota null označuje nezávislost národního prostředí.</span><span class="sxs-lookup"><span data-stu-id="50922-121">A null value indicates locale independence.</span></span> <span data-ttu-id="50922-122">**Poznámka:**  Ve .NET Framework verze 1,0 nemůžete zadat více než jedno národní prostředí.</span><span class="sxs-lookup"><span data-stu-id="50922-122">**Note:**  In the .NET Framework version 1.0 you cannot specify more than one locale.</span></span>|  
|`cbLocale`|<span data-ttu-id="50922-123">Velikost v různých znacích `szLocale`.</span><span class="sxs-lookup"><span data-stu-id="50922-123">The size in wide characters of `szLocale`.</span></span>|  
|`rdwProcessor`|<span data-ttu-id="50922-124">Pole identifikátorů, jak je definováno v souboru Winnt. h pro typy procesorů, které jsou podporovány odkazovaným sestavením.</span><span class="sxs-lookup"><span data-stu-id="50922-124">An array of identifiers, as defined in Winnt.h, for the processor types that are supported by the referenced assembly.</span></span> <span data-ttu-id="50922-125">Hodnota NULL označuje nezávislost procesoru.</span><span class="sxs-lookup"><span data-stu-id="50922-125">A NULL value indicates processor independence.</span></span>|  
|`ulProcessor`|<span data-ttu-id="50922-126">Délka pole `rdwProcessor`.</span><span class="sxs-lookup"><span data-stu-id="50922-126">The length of the `rdwProcessor` array.</span></span>|  
|`rOS`|<span data-ttu-id="50922-127">Pole instancí [OSINFO –](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) určujících operační systémy, které jsou podporovány odkazovaným sestavením.</span><span class="sxs-lookup"><span data-stu-id="50922-127">An array of [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) instances specifying the operating systems that are supported by the referenced assembly.</span></span> <span data-ttu-id="50922-128">Hodnota NULL označuje nezávislost operačního systému.</span><span class="sxs-lookup"><span data-stu-id="50922-128">A NULL value indicates operating-system independence.</span></span>|  
|`ulOS`|<span data-ttu-id="50922-129">Délka pole `rOS`.</span><span class="sxs-lookup"><span data-stu-id="50922-129">The length of the `rOS` array.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="50922-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="50922-130">Requirements</span></span>  
 <span data-ttu-id="50922-131">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50922-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50922-132">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="50922-132">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="50922-133">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="50922-133">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="50922-134">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50922-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50922-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50922-135">See also</span></span>

- [<span data-ttu-id="50922-136">Struktury pro metadata</span><span class="sxs-lookup"><span data-stu-id="50922-136">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="50922-137">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="50922-137">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="50922-138">OSINFO – struktura</span><span class="sxs-lookup"><span data-stu-id="50922-138">OSINFO Structure</span></span>](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)
