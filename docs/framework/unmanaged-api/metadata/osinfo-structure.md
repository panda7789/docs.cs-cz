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
ms.openlocfilehash: 048fe687e4d979576896f5310bddc855b40bb695
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175223"
---
# <a name="osinfo-structure"></a><span data-ttu-id="8d75e-102">OSINFO – struktura</span><span class="sxs-lookup"><span data-stu-id="8d75e-102">OSINFO Structure</span></span>
<span data-ttu-id="8d75e-103">Obsahuje podrobnosti o operačním systému pro sestavení nebo modul.</span><span class="sxs-lookup"><span data-stu-id="8d75e-103">Contains details about the operating system for an assembly or module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d75e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d75e-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;
    DWORD   dwOSMinorVersion;
} OSINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="8d75e-105">Členové</span><span class="sxs-lookup"><span data-stu-id="8d75e-105">Members</span></span>  
  
|<span data-ttu-id="8d75e-106">Člen</span><span class="sxs-lookup"><span data-stu-id="8d75e-106">Member</span></span>|<span data-ttu-id="8d75e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8d75e-107">Description</span></span>|  
|------------|-----------------|  
|`dwOSPlatformId`|<span data-ttu-id="8d75e-108">Jedna z hodnot identifikátorů definovaných `GetVersionEx`funkcí platformy Microsoft Windows .</span><span class="sxs-lookup"><span data-stu-id="8d75e-108">One of the identifier values defined by the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="8d75e-109">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="8d75e-109">The following values are supported:</span></span><br /><br /> <span data-ttu-id="8d75e-110">- VER_PLATFORM_WIN32s, nebo 0x0000, určit Microsoft Windows 3.1.</span><span class="sxs-lookup"><span data-stu-id="8d75e-110">-   VER_PLATFORM_WIN32s, or 0x0000, to specify Microsoft Windows 3.1.</span></span><br /><span data-ttu-id="8d75e-111">- VER_PLATFORM_WIN32_WINDOWS nebo 0x0001, chcete-li zadat windows 95, Windows 98 nebo operační systémy pocházející z nich.</span><span class="sxs-lookup"><span data-stu-id="8d75e-111">-   VER_PLATFORM_WIN32_WINDOWS, or 0x0001, to specify Windows 95, Windows 98, or operating systems descended from them.</span></span><br /><span data-ttu-id="8d75e-112">- VER_PLATFORM_WIN32_NT nebo 0x0002, chcete-li zadat systém Windows NT nebo operační systémy pocházející z něj.</span><span class="sxs-lookup"><span data-stu-id="8d75e-112">-   VER_PLATFORM_WIN32_NT, or 0x0002, to specify Windows NT or operating systems descended from it.</span></span>|  
|`dwOSMajorVersion`|<span data-ttu-id="8d75e-113">Hlavní verze operačního systému nebo hodnota NULL označující libovolnou verzi.</span><span class="sxs-lookup"><span data-stu-id="8d75e-113">The operating system major version, or a NULL value to indicate any version.</span></span>|  
|`dwOSMinorVersion`|<span data-ttu-id="8d75e-114">Dílčí verze operačního systému nebo hodnota NULL označující libovolnou verzi.</span><span class="sxs-lookup"><span data-stu-id="8d75e-114">The operating system minor version, or a NULL value to indicate any version.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d75e-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8d75e-115">Remarks</span></span>  
 <span data-ttu-id="8d75e-116">`OSINFO`Je založen `OSVERSIONINFOEX` na struktuře, která se používá `GetVersionEx`při volání funkce platformy Microsoft Windows .</span><span class="sxs-lookup"><span data-stu-id="8d75e-116">`OSINFO` is based on the `OSVERSIONINFOEX` structure that is used in calls to the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="8d75e-117">Tato struktura se používá assemblymetadata struktury k označení jeho podporu operačního systému.</span><span class="sxs-lookup"><span data-stu-id="8d75e-117">This structure is used by the ASSEMBLYMETADATA structure to indicate its operating system support.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d75e-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8d75e-118">Requirements</span></span>  
 <span data-ttu-id="8d75e-119">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d75e-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d75e-120">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="8d75e-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8d75e-121">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8d75e-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8d75e-122">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d75e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d75e-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="8d75e-123">See also</span></span>

- [<span data-ttu-id="8d75e-124">Struktury pro metadata</span><span class="sxs-lookup"><span data-stu-id="8d75e-124">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="8d75e-125">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d75e-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
