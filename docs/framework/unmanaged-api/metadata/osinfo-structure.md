---
title: "OSINFO – struktura"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dd30fe7904fa6c0685dd9c39931cc545e4e30583
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="osinfo-structure"></a><span data-ttu-id="5bfa1-102">OSINFO – struktura</span><span class="sxs-lookup"><span data-stu-id="5bfa1-102">OSINFO Structure</span></span>
<span data-ttu-id="5bfa1-103">Obsahuje podrobné informace o operačním systému pro modul nebo sestavení.</span><span class="sxs-lookup"><span data-stu-id="5bfa1-103">Contains details about the operating system for an assembly or module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bfa1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5bfa1-104">Syntax</span></span>  
  
```  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;   
    DWORD   dwOSMinorVersion;   
} OSINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="5bfa1-105">Členové</span><span class="sxs-lookup"><span data-stu-id="5bfa1-105">Members</span></span>  
  
|<span data-ttu-id="5bfa1-106">Člen</span><span class="sxs-lookup"><span data-stu-id="5bfa1-106">Member</span></span>|<span data-ttu-id="5bfa1-107">Popis</span><span class="sxs-lookup"><span data-stu-id="5bfa1-107">Description</span></span>|  
|------------|-----------------|  
|`dwOSPlatformId`|<span data-ttu-id="5bfa1-108">Jedna z hodnot identifikátoru definovaných funkcí platformy Microsoft Windows `GetVersionEx`.</span><span class="sxs-lookup"><span data-stu-id="5bfa1-108">One of the identifier values defined by the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="5bfa1-109">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="5bfa1-109">The following values are supported:</span></span><br /><br /> <span data-ttu-id="5bfa1-110">-VER_PLATFORM_WIN32s, nebo 0x0000, zadejte systému Windows 3.1.</span><span class="sxs-lookup"><span data-stu-id="5bfa1-110">-   VER_PLATFORM_WIN32s, or 0x0000, to specify Microsoft Windows 3.1.</span></span><br /><span data-ttu-id="5bfa1-111">-VER_PLATFORM_WIN32_WINDOWS, nebo 0x0001, a zadejte systému Windows 95, Windows 98 nebo operační systémy jejich následníky.</span><span class="sxs-lookup"><span data-stu-id="5bfa1-111">-   VER_PLATFORM_WIN32_WINDOWS, or 0x0001, to specify Windows 95, Windows 98, or operating systems descended from them.</span></span><br /><span data-ttu-id="5bfa1-112">-VER_PLATFORM_WIN32_NT, nebo 0x0010, určete systému Windows NT nebo operační systémy jeho následníky.</span><span class="sxs-lookup"><span data-stu-id="5bfa1-112">-   VER_PLATFORM_WIN32_NT, or 0x0010, to specify Windows NT or operating systems descended from it.</span></span>|  
|`dwOSMajorVersion`|<span data-ttu-id="5bfa1-113">Hlavní verze operačního systému, nebo hodnota NULL označíte, všechny verze.</span><span class="sxs-lookup"><span data-stu-id="5bfa1-113">The operating system major version, or a NULL value to indicate any version.</span></span>|  
|`dwOSMinorVersion`|<span data-ttu-id="5bfa1-114">Podverze operačního systému, nebo hodnota NULL označíte, všechny verze.</span><span class="sxs-lookup"><span data-stu-id="5bfa1-114">The operating system minor version, or a NULL value to indicate any version.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5bfa1-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5bfa1-115">Remarks</span></span>  
 <span data-ttu-id="5bfa1-116">`OSINFO`je založena na `OSVERSIONINFOEX` struktury tedy použité ve volání funkce platformy Microsoft Windows `GetVersionEx`.</span><span class="sxs-lookup"><span data-stu-id="5bfa1-116">`OSINFO` is based on the `OSVERSIONINFOEX` structure that is used in calls to the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="5bfa1-117">Tato struktura je pomocí assemblymetadata – struktura slouží k určení jeho podporu operačního systému.</span><span class="sxs-lookup"><span data-stu-id="5bfa1-117">This structure is used by the ASSEMBLYMETADATA structure to indicate its operating system support.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bfa1-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5bfa1-118">Requirements</span></span>  
 <span data-ttu-id="5bfa1-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bfa1-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bfa1-120">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5bfa1-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5bfa1-121">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5bfa1-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5bfa1-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bfa1-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bfa1-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="5bfa1-123">See Also</span></span>  
 [<span data-ttu-id="5bfa1-124">Struktury pro metadata</span><span class="sxs-lookup"><span data-stu-id="5bfa1-124">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [<span data-ttu-id="5bfa1-125">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5bfa1-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
