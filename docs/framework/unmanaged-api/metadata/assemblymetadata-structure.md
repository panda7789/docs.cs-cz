---
title: "ASSEMBLYMETADATA – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ASSEMBLYMETADATA
api_location: mscoree.dll
api_type: COM
f1_keywords: ASSEMBLYMETADATA
helpviewer_keywords: ASSEMBLYMETADATA structure [.NET Framework metadata]
ms.assetid: 1af98e57-9145-4d35-bb78-77d1da7c91a5
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5652907abc17868414c554cb5c87b0856d2c5a0c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="assemblymetadata-structure"></a><span data-ttu-id="90c19-102">ASSEMBLYMETADATA – struktura</span><span class="sxs-lookup"><span data-stu-id="90c19-102">ASSEMBLYMETADATA Structure</span></span>
<span data-ttu-id="90c19-103">Obsahuje informace o odkazované sestavení, včetně jeho verzi a jeho úrovně podpory pro národní prostředí, procesory a operační systémy.</span><span class="sxs-lookup"><span data-stu-id="90c19-103">Contains information about the referenced assembly, including its version and its level of support for locales, processors, and operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90c19-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90c19-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="90c19-105">Členové</span><span class="sxs-lookup"><span data-stu-id="90c19-105">Members</span></span>  
  
|<span data-ttu-id="90c19-106">Člen</span><span class="sxs-lookup"><span data-stu-id="90c19-106">Member</span></span>|<span data-ttu-id="90c19-107">Popis</span><span class="sxs-lookup"><span data-stu-id="90c19-107">Description</span></span>|  
|------------|-----------------|  
|`usMajorVersion`|<span data-ttu-id="90c19-108">Hlavní číslo verze odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="90c19-108">The major version number of the referenced assembly.</span></span> <span data-ttu-id="90c19-109">Tato hodnota nemůže být nula.</span><span class="sxs-lookup"><span data-stu-id="90c19-109">This value cannot be zero.</span></span> <span data-ttu-id="90c19-110">Pokud všechny bity `usMajorVersion` jsou nastavené, není zadán hlavní verzi.</span><span class="sxs-lookup"><span data-stu-id="90c19-110">If all the bits of `usMajorVersion` are set, the major version is not specified.</span></span>|  
|`usMinorVersion`|<span data-ttu-id="90c19-111">Číslo podverze odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="90c19-111">The minor version number of the referenced assembly.</span></span> <span data-ttu-id="90c19-112">Tato hodnota nemůže být nula.</span><span class="sxs-lookup"><span data-stu-id="90c19-112">This value cannot be zero.</span></span> <span data-ttu-id="90c19-113">Pokud všechny bity `usMinorVersion` jsou nastavené na podverzi není zadán.</span><span class="sxs-lookup"><span data-stu-id="90c19-113">If all the bits of `usMinorVersion` are set, the minor version is not specified.</span></span>|  
|`usBuildNumber`|<span data-ttu-id="90c19-114">Číslo sestavení odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="90c19-114">The build number of the referenced assembly.</span></span> <span data-ttu-id="90c19-115">Tato hodnota nemůže být nula.</span><span class="sxs-lookup"><span data-stu-id="90c19-115">This value cannot be zero.</span></span> <span data-ttu-id="90c19-116">Pokud všechny bity `usBuildNumber` jsou nastavené, číslo sestavení není zadán.</span><span class="sxs-lookup"><span data-stu-id="90c19-116">If all the bits of `usBuildNumber` are set, the build number is not specified.</span></span>|  
|`usRevisionNumber`|<span data-ttu-id="90c19-117">Číslo revize odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="90c19-117">The revision number of the referenced assembly.</span></span> <span data-ttu-id="90c19-118">Tato hodnota nemůže být nula.</span><span class="sxs-lookup"><span data-stu-id="90c19-118">This value cannot be zero.</span></span> <span data-ttu-id="90c19-119">Pokud všechny bity `usRevisionNumber` jsou nastavené, číslo revize není zadán.</span><span class="sxs-lookup"><span data-stu-id="90c19-119">If all the bits of `usRevisionNumber` are set, the revision number is not specified.</span></span>|  
|`szLocale`|<span data-ttu-id="90c19-120">Seznam názvů národní prostředí podle specifikace RFC1766, oddělené středníky, zadání národní prostředí nepodporuje odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="90c19-120">A list of locale names conforming to the RFC1766 specification, separated by semicolons, specifying the locales supported by the referenced assembly.</span></span> <span data-ttu-id="90c19-121">Hodnota null určuje nezávislost národního prostředí.</span><span class="sxs-lookup"><span data-stu-id="90c19-121">A null value indicates locale independence.</span></span> <span data-ttu-id="90c19-122">**Poznámka:** v rozhraní .NET Framework verze 1.0 nelze zadat více než jeden národního prostředí.</span><span class="sxs-lookup"><span data-stu-id="90c19-122">**Note:**  In the .NET Framework version 1.0 you cannot specify more than one locale.</span></span>|  
|`cbLocale`|<span data-ttu-id="90c19-123">Velikost v široké znaky `szLocale`.</span><span class="sxs-lookup"><span data-stu-id="90c19-123">The size in wide characters of `szLocale`.</span></span>|  
|`rdwProcessor`|<span data-ttu-id="90c19-124">Pole identifikátory, jak jsou definovány v souboru Winnt.h, pro typy procesoru, které jsou podporovány odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="90c19-124">An array of identifiers, as defined in Winnt.h, for the processor types that are supported by the referenced assembly.</span></span> <span data-ttu-id="90c19-125">Hodnota NULL určuje nezávislost procesoru.</span><span class="sxs-lookup"><span data-stu-id="90c19-125">A NULL value indicates processor independence.</span></span>|  
|`ulProcessor`|<span data-ttu-id="90c19-126">Délka `rdwProcessor` pole.</span><span class="sxs-lookup"><span data-stu-id="90c19-126">The length of the `rdwProcessor` array.</span></span>|  
|`rOS`|<span data-ttu-id="90c19-127">Pole [osinfo –](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) instance zadání operační systémy, které jsou podporovány odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="90c19-127">An array of [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) instances specifying the operating systems that are supported by the referenced assembly.</span></span> <span data-ttu-id="90c19-128">Hodnota NULL znamená nezávislost operačního systému.</span><span class="sxs-lookup"><span data-stu-id="90c19-128">A NULL value indicates operating-system independence.</span></span>|  
|`ulOS`|<span data-ttu-id="90c19-129">Délka `rOS` pole.</span><span class="sxs-lookup"><span data-stu-id="90c19-129">The length of the `rOS` array.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="90c19-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="90c19-130">Requirements</span></span>  
 <span data-ttu-id="90c19-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90c19-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90c19-132">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="90c19-132">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="90c19-133">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="90c19-133">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="90c19-134">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90c19-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90c19-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="90c19-135">See Also</span></span>  
 [<span data-ttu-id="90c19-136">Struktury metadat</span><span class="sxs-lookup"><span data-stu-id="90c19-136">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [<span data-ttu-id="90c19-137">Imetadataassemblyemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90c19-137">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="90c19-138">Osinfo – struktura</span><span class="sxs-lookup"><span data-stu-id="90c19-138">OSINFO Structure</span></span>](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)
