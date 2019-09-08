---
title: ASSEMBLY_INFO – struktura
ms.date: 03/30/2017
api_name:
- ASSEMBLY_INFO
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASSEMBLY_INFO
helpviewer_keywords:
- ASSEMBLY_INFO structure [.NET Framework fusion]
ms.assetid: b3cbb47c-457f-4083-8895-49562ca99ab8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 390ab4881396bbc01337d087f05b6066153bfed1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795484"
---
# <a name="assembly_info-structure"></a><span data-ttu-id="d290a-102">ASSEMBLY_INFO – struktura</span><span class="sxs-lookup"><span data-stu-id="d290a-102">ASSEMBLY_INFO Structure</span></span>
<span data-ttu-id="d290a-103">Obsahuje informace o sestavení, které je registrováno v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="d290a-103">Contains information about an assembly that is registered in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d290a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d290a-104">Syntax</span></span>  
  
```cpp  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="d290a-105">Členové</span><span class="sxs-lookup"><span data-stu-id="d290a-105">Members</span></span>  
  
|<span data-ttu-id="d290a-106">Člen</span><span class="sxs-lookup"><span data-stu-id="d290a-106">Member</span></span>|<span data-ttu-id="d290a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d290a-107">Description</span></span>|  
|------------|-----------------|  
|`cbAssemblyInfo`|<span data-ttu-id="d290a-108">Velikost struktury v bajtech.</span><span class="sxs-lookup"><span data-stu-id="d290a-108">The size, in bytes, of the structure.</span></span> <span data-ttu-id="d290a-109">Toto pole je vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="d290a-109">This field is reserved for future extensibility.</span></span>|  
|`dwAssemblyFlags`|<span data-ttu-id="d290a-110">Příznaky, které označují podrobnosti o instalaci sestavení.</span><span class="sxs-lookup"><span data-stu-id="d290a-110">Flags that indicate installation details about the assembly.</span></span> <span data-ttu-id="d290a-111">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="d290a-111">The following values are supported:</span></span><br /><br /> <span data-ttu-id="d290a-112">– Hodnota ASSEMBLYINFO_FLAG_INSTALLED, která označuje, že sestavení je nainstalováno.</span><span class="sxs-lookup"><span data-stu-id="d290a-112">-   The ASSEMBLYINFO_FLAG_INSTALLED value, which indicates that the assembly is installed.</span></span> <span data-ttu-id="d290a-113">Aktuální verze .NET Framework vždy nastavuje `dwAssemblyFlags` na tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d290a-113">The current version of the .NET Framework always sets `dwAssemblyFlags` to this value.</span></span><br /><span data-ttu-id="d290a-114">– Hodnota ASSEMBLYINFO_FLAG_PAYLOADRESIDENT, která označuje, že sestavení je rezidentní v datové části.</span><span class="sxs-lookup"><span data-stu-id="d290a-114">-   The ASSEMBLYINFO_FLAG_PAYLOADRESIDENT value, which indicates that the assembly is a payload resident.</span></span> <span data-ttu-id="d290a-115">Aktuální verze .NET Framework se nikdy nenastavuje `dwAssemblyFlags` na tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d290a-115">The current version of the .NET Framework never sets `dwAssemblyFlags` to this value.</span></span>|  
|`uliAssemblySizeInKB`|<span data-ttu-id="d290a-116">Celková velikost souborů, které sestavení obsahuje, v kilobajtech.</span><span class="sxs-lookup"><span data-stu-id="d290a-116">The total size, in kilobytes, of the files that the assembly contains.</span></span>|  
|`pszCurrentAssemblyPathBuf`|<span data-ttu-id="d290a-117">Ukazatel na vyrovnávací paměť řetězce, který obsahuje aktuální cestu k souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="d290a-117">A pointer to a string buffer that holds the current path to the manifest file.</span></span> <span data-ttu-id="d290a-118">Cesta musí končit znakem null.</span><span class="sxs-lookup"><span data-stu-id="d290a-118">The path must end with a null character.</span></span>|  
|`cchBuf`|<span data-ttu-id="d290a-119">Počet velkých znaků, včetně ukončovacího znaku null, který `pszCurrentAssemblyPathBuf` obsahuje.</span><span class="sxs-lookup"><span data-stu-id="d290a-119">The number of wide characters, including the null terminator, that `pszCurrentAssemblyPathBuf` contains.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d290a-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d290a-120">Requirements</span></span>  
 <span data-ttu-id="d290a-121">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d290a-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d290a-122">**Hlaviček** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="d290a-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d290a-123">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d290a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d290a-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d290a-124">See also</span></span>

- [<span data-ttu-id="d290a-125">Struktury pro fúze</span><span class="sxs-lookup"><span data-stu-id="d290a-125">Fusion Structures</span></span>](fusion-structures.md)
- [<span data-ttu-id="d290a-126">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="d290a-126">Global Assembly Cache</span></span>](../../app-domains/gac.md)
