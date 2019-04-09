---
title: OSINFO – struktura
ms.date: 03/30/2017
api_name:
- OSINFO
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- OSINFO
helpviewer_keywords:
- OSINFO structure [.NET Framework metadata]
ms.assetid: fac7b480-7adb-4450-a5e9-690fed81ffae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0aba49fb4a60b2e471c541a8d8531a1cbc8627f9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096196"
---
# <a name="osinfo-structure"></a><span data-ttu-id="44d7d-102">OSINFO – struktura</span><span class="sxs-lookup"><span data-stu-id="44d7d-102">OSINFO Structure</span></span>
<span data-ttu-id="44d7d-103">Obsahuje podrobnosti o operačním systému pro sestavení nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="44d7d-103">Contains details about the operating system for an assembly or module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44d7d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44d7d-104">Syntax</span></span>  
  
```  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;   
    DWORD   dwOSMinorVersion;   
} OSINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="44d7d-105">Členové</span><span class="sxs-lookup"><span data-stu-id="44d7d-105">Members</span></span>  
  
|<span data-ttu-id="44d7d-106">Člen</span><span class="sxs-lookup"><span data-stu-id="44d7d-106">Member</span></span>|<span data-ttu-id="44d7d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="44d7d-107">Description</span></span>|  
|------------|-----------------|  
|`dwOSPlatformId`|<span data-ttu-id="44d7d-108">Jedna z hodnot identifikátoru definovaných funkcí platformy Microsoft Windows `GetVersionEx`.</span><span class="sxs-lookup"><span data-stu-id="44d7d-108">One of the identifier values defined by the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="44d7d-109">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="44d7d-109">The following values are supported:</span></span><br /><br /> <span data-ttu-id="44d7d-110">-VER_PLATFORM_WIN32s, nebo 0x0000, chcete-li určit instalační služba systému Windows 3.1.</span><span class="sxs-lookup"><span data-stu-id="44d7d-110">-   VER_PLATFORM_WIN32s, or 0x0000, to specify Microsoft Windows 3.1.</span></span><br /><span data-ttu-id="44d7d-111">-VER_PLATFORM_WIN32_WINDOWS, nebo 0x0001, zadejte operační systémy Windows 95, Windows 98 nebo který z nich.</span><span class="sxs-lookup"><span data-stu-id="44d7d-111">-   VER_PLATFORM_WIN32_WINDOWS, or 0x0001, to specify Windows 95, Windows 98, or operating systems descended from them.</span></span><br /><span data-ttu-id="44d7d-112">-VER_PLATFORM_WIN32_NT, nebo změnu 0x0010, Windows NT nebo operační systémy, který z něj.</span><span class="sxs-lookup"><span data-stu-id="44d7d-112">-   VER_PLATFORM_WIN32_NT, or 0x0010, to specify Windows NT or operating systems descended from it.</span></span>|  
|`dwOSMajorVersion`|<span data-ttu-id="44d7d-113">Hlavní verze operačního systému, nebo hodnota NULL označuje všechny verze.</span><span class="sxs-lookup"><span data-stu-id="44d7d-113">The operating system major version, or a NULL value to indicate any version.</span></span>|  
|`dwOSMinorVersion`|<span data-ttu-id="44d7d-114">Podverze operačního systému, nebo hodnota NULL označuje všechny verze.</span><span class="sxs-lookup"><span data-stu-id="44d7d-114">The operating system minor version, or a NULL value to indicate any version.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44d7d-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="44d7d-115">Remarks</span></span>  
 `OSINFO` <span data-ttu-id="44d7d-116">vychází `OSVERSIONINFOEX` struktury, který je použité ve volání funkce platformy Microsoft Windows `GetVersionEx`.</span><span class="sxs-lookup"><span data-stu-id="44d7d-116">is based on the `OSVERSIONINFOEX` structure that is used in calls to the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="44d7d-117">Tato struktura používá assemblymetadata – struktura označující jeho podporu operačního systému.</span><span class="sxs-lookup"><span data-stu-id="44d7d-117">This structure is used by the ASSEMBLYMETADATA structure to indicate its operating system support.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44d7d-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="44d7d-118">Requirements</span></span>  
 <span data-ttu-id="44d7d-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44d7d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44d7d-120">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="44d7d-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="44d7d-121">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="44d7d-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="44d7d-122">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="44d7d-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="44d7d-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="44d7d-123">See also</span></span>

- [<span data-ttu-id="44d7d-124">Struktury metadat</span><span class="sxs-lookup"><span data-stu-id="44d7d-124">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="44d7d-125">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="44d7d-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
