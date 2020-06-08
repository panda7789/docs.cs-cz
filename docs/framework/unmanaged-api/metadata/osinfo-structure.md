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
ms.openlocfilehash: ab9d7eb6f5760b43fe805443bbe1ea4a95c72069
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501063"
---
# <a name="osinfo-structure"></a><span data-ttu-id="52f53-102">OSINFO – struktura</span><span class="sxs-lookup"><span data-stu-id="52f53-102">OSINFO Structure</span></span>
<span data-ttu-id="52f53-103">Obsahuje podrobnosti o operačním systému pro sestavení nebo modul.</span><span class="sxs-lookup"><span data-stu-id="52f53-103">Contains details about the operating system for an assembly or module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52f53-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52f53-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;
    DWORD   dwOSMinorVersion;
} OSINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="52f53-105">Členové</span><span class="sxs-lookup"><span data-stu-id="52f53-105">Members</span></span>  
  
|<span data-ttu-id="52f53-106">Člen</span><span class="sxs-lookup"><span data-stu-id="52f53-106">Member</span></span>|<span data-ttu-id="52f53-107">Description</span><span class="sxs-lookup"><span data-stu-id="52f53-107">Description</span></span>|  
|------------|-----------------|  
|`dwOSPlatformId`|<span data-ttu-id="52f53-108">Jedna z hodnot identifikátoru definovaná funkcí platformy Microsoft Windows `GetVersionEx`</span><span class="sxs-lookup"><span data-stu-id="52f53-108">One of the identifier values defined by the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="52f53-109">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="52f53-109">The following values are supported:</span></span><br /><br /> <span data-ttu-id="52f53-110">-VER_PLATFORM_WIN32s nebo 0x0000, pokud chcete zadat Microsoft Windows 3,1.</span><span class="sxs-lookup"><span data-stu-id="52f53-110">-   VER_PLATFORM_WIN32s, or 0x0000, to specify Microsoft Windows 3.1.</span></span><br /><span data-ttu-id="52f53-111">-VER_PLATFORM_WIN32_WINDOWS nebo 0x0001, chcete-li určit systémy Windows 95, Windows 98 nebo operační systémy, které jsou z nich pořízené.</span><span class="sxs-lookup"><span data-stu-id="52f53-111">-   VER_PLATFORM_WIN32_WINDOWS, or 0x0001, to specify Windows 95, Windows 98, or operating systems descended from them.</span></span><br /><span data-ttu-id="52f53-112">-VER_PLATFORM_WIN32_NT nebo 0x0002, chcete-li určit systémy Windows NT nebo operační systémy, které jsou z něj pořízené.</span><span class="sxs-lookup"><span data-stu-id="52f53-112">-   VER_PLATFORM_WIN32_NT, or 0x0002, to specify Windows NT or operating systems descended from it.</span></span>|  
|`dwOSMajorVersion`|<span data-ttu-id="52f53-113">Hlavní verze operačního systému nebo hodnota NULL k označení libovolné verze.</span><span class="sxs-lookup"><span data-stu-id="52f53-113">The operating system major version, or a NULL value to indicate any version.</span></span>|  
|`dwOSMinorVersion`|<span data-ttu-id="52f53-114">Dílčí verze operačního systému nebo hodnota NULL k označení libovolné verze.</span><span class="sxs-lookup"><span data-stu-id="52f53-114">The operating system minor version, or a NULL value to indicate any version.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52f53-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="52f53-115">Remarks</span></span>  
 <span data-ttu-id="52f53-116">`OSINFO`vychází ze `OSVERSIONINFOEX` struktury používané při volání funkce platformy Microsoft Windows `GetVersionEx` .</span><span class="sxs-lookup"><span data-stu-id="52f53-116">`OSINFO` is based on the `OSVERSIONINFOEX` structure that is used in calls to the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="52f53-117">Tato struktura je používána strukturou AssemblyMetadata – k označení podpory operačního systému.</span><span class="sxs-lookup"><span data-stu-id="52f53-117">This structure is used by the ASSEMBLYMETADATA structure to indicate its operating system support.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52f53-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="52f53-118">Requirements</span></span>  
 <span data-ttu-id="52f53-119">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52f53-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52f53-120">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="52f53-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="52f53-121">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="52f53-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="52f53-122">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52f53-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52f53-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="52f53-123">See also</span></span>

- [<span data-ttu-id="52f53-124">Struktury pro metadata</span><span class="sxs-lookup"><span data-stu-id="52f53-124">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="52f53-125">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="52f53-125">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
