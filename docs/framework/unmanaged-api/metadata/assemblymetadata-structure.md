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
ms.openlocfilehash: 5c7211fc2523b70313a1e4d4d9d2da0dcecd1d32
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009428"
---
# <a name="assemblymetadata-structure"></a><span data-ttu-id="811fe-102">ASSEMBLYMETADATA – struktura</span><span class="sxs-lookup"><span data-stu-id="811fe-102">ASSEMBLYMETADATA Structure</span></span>
<span data-ttu-id="811fe-103">Obsahuje informace o odkazovaném sestavení, včetně jeho verze a jeho úrovně podpory pro národní prostředí, procesory a operační systémy.</span><span class="sxs-lookup"><span data-stu-id="811fe-103">Contains information about the referenced assembly, including its version and its level of support for locales, processors, and operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="811fe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="811fe-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="811fe-105">Členové</span><span class="sxs-lookup"><span data-stu-id="811fe-105">Members</span></span>  
  
|<span data-ttu-id="811fe-106">Člen</span><span class="sxs-lookup"><span data-stu-id="811fe-106">Member</span></span>|<span data-ttu-id="811fe-107">Description</span><span class="sxs-lookup"><span data-stu-id="811fe-107">Description</span></span>|  
|------------|-----------------|  
|`usMajorVersion`|<span data-ttu-id="811fe-108">Hlavní číslo verze odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="811fe-108">The major version number of the referenced assembly.</span></span> <span data-ttu-id="811fe-109">Tato hodnota nemůže být nulová.</span><span class="sxs-lookup"><span data-stu-id="811fe-109">This value cannot be zero.</span></span> <span data-ttu-id="811fe-110">Pokud jsou nastaveny všechny bity `usMajorVersion` , není hlavní verze určena.</span><span class="sxs-lookup"><span data-stu-id="811fe-110">If all the bits of `usMajorVersion` are set, the major version is not specified.</span></span>|  
|`usMinorVersion`|<span data-ttu-id="811fe-111">Číslo dílčí verze odkazovaného sestavení</span><span class="sxs-lookup"><span data-stu-id="811fe-111">The minor version number of the referenced assembly.</span></span> <span data-ttu-id="811fe-112">Tato hodnota nemůže být nulová.</span><span class="sxs-lookup"><span data-stu-id="811fe-112">This value cannot be zero.</span></span> <span data-ttu-id="811fe-113">Pokud jsou nastaveny všechny bity `usMinorVersion` , není podverze určena.</span><span class="sxs-lookup"><span data-stu-id="811fe-113">If all the bits of `usMinorVersion` are set, the minor version is not specified.</span></span>|  
|`usBuildNumber`|<span data-ttu-id="811fe-114">Číslo sestavení odkazovaného sestavení</span><span class="sxs-lookup"><span data-stu-id="811fe-114">The build number of the referenced assembly.</span></span> <span data-ttu-id="811fe-115">Tato hodnota nemůže být nulová.</span><span class="sxs-lookup"><span data-stu-id="811fe-115">This value cannot be zero.</span></span> <span data-ttu-id="811fe-116">Pokud jsou nastaveny všechny bity `usBuildNumber` , číslo sestavení není zadáno.</span><span class="sxs-lookup"><span data-stu-id="811fe-116">If all the bits of `usBuildNumber` are set, the build number is not specified.</span></span>|  
|`usRevisionNumber`|<span data-ttu-id="811fe-117">Číslo revize odkazovaného sestavení</span><span class="sxs-lookup"><span data-stu-id="811fe-117">The revision number of the referenced assembly.</span></span> <span data-ttu-id="811fe-118">Tato hodnota nemůže být nulová.</span><span class="sxs-lookup"><span data-stu-id="811fe-118">This value cannot be zero.</span></span> <span data-ttu-id="811fe-119">Pokud jsou nastaveny všechny bity `usRevisionNumber` , číslo revize není zadáno.</span><span class="sxs-lookup"><span data-stu-id="811fe-119">If all the bits of `usRevisionNumber` are set, the revision number is not specified.</span></span>|  
|`szLocale`|<span data-ttu-id="811fe-120">Seznam názvů národních prostředí, které odpovídají specifikaci RFC1766, oddělený středníky a určením národních prostředí podporovaných odkazovaným sestavením.</span><span class="sxs-lookup"><span data-stu-id="811fe-120">A list of locale names conforming to the RFC1766 specification, separated by semicolons, specifying the locales supported by the referenced assembly.</span></span> <span data-ttu-id="811fe-121">Hodnota null označuje nezávislost národního prostředí.</span><span class="sxs-lookup"><span data-stu-id="811fe-121">A null value indicates locale independence.</span></span> <span data-ttu-id="811fe-122">**Poznámka:**  Ve .NET Framework verze 1,0 nemůžete zadat více než jedno národní prostředí.</span><span class="sxs-lookup"><span data-stu-id="811fe-122">**Note:**  In the .NET Framework version 1.0 you cannot specify more than one locale.</span></span>|  
|`cbLocale`|<span data-ttu-id="811fe-123">Velikost v různých znacích `szLocale` .</span><span class="sxs-lookup"><span data-stu-id="811fe-123">The size in wide characters of `szLocale`.</span></span>|  
|`rdwProcessor`|<span data-ttu-id="811fe-124">Pole identifikátorů, jak je definováno v souboru Winnt. h pro typy procesorů, které jsou podporovány odkazovaným sestavením.</span><span class="sxs-lookup"><span data-stu-id="811fe-124">An array of identifiers, as defined in Winnt.h, for the processor types that are supported by the referenced assembly.</span></span> <span data-ttu-id="811fe-125">Hodnota NULL označuje nezávislost procesoru.</span><span class="sxs-lookup"><span data-stu-id="811fe-125">A NULL value indicates processor independence.</span></span>|  
|`ulProcessor`|<span data-ttu-id="811fe-126">Délka `rdwProcessor` pole.</span><span class="sxs-lookup"><span data-stu-id="811fe-126">The length of the `rdwProcessor` array.</span></span>|  
|`rOS`|<span data-ttu-id="811fe-127">Pole instancí [OSINFO –](osinfo-structure.md) určujících operační systémy, které jsou podporovány odkazovaným sestavením.</span><span class="sxs-lookup"><span data-stu-id="811fe-127">An array of [OSINFO](osinfo-structure.md) instances specifying the operating systems that are supported by the referenced assembly.</span></span> <span data-ttu-id="811fe-128">Hodnota NULL označuje nezávislost operačního systému.</span><span class="sxs-lookup"><span data-stu-id="811fe-128">A NULL value indicates operating-system independence.</span></span>|  
|`ulOS`|<span data-ttu-id="811fe-129">Délka `rOS` pole.</span><span class="sxs-lookup"><span data-stu-id="811fe-129">The length of the `rOS` array.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="811fe-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="811fe-130">Requirements</span></span>  
 <span data-ttu-id="811fe-131">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="811fe-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="811fe-132">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="811fe-132">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="811fe-133">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="811fe-133">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="811fe-134">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="811fe-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="811fe-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="811fe-135">See also</span></span>

- [<span data-ttu-id="811fe-136">Struktury pro metadata</span><span class="sxs-lookup"><span data-stu-id="811fe-136">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="811fe-137">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="811fe-137">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="811fe-138">OSINFO – struktura</span><span class="sxs-lookup"><span data-stu-id="811fe-138">OSINFO Structure</span></span>](osinfo-structure.md)
