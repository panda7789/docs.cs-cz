---
title: "ASSEMBLY_INFO – struktura"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 215d80c3d207c2f50cfbd74386915b0467692b57
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="assemblyinfo-structure"></a><span data-ttu-id="e6c5d-102">ASSEMBLY_INFO – struktura</span><span class="sxs-lookup"><span data-stu-id="e6c5d-102">ASSEMBLY_INFO Structure</span></span>
<span data-ttu-id="e6c5d-103">Obsahuje informace o sestavení, které je zaregistrován v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="e6c5d-103">Contains information about an assembly that is registered in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6c5d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6c5d-104">Syntax</span></span>  
  
```  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="e6c5d-105">Členové</span><span class="sxs-lookup"><span data-stu-id="e6c5d-105">Members</span></span>  
  
|<span data-ttu-id="e6c5d-106">Člen</span><span class="sxs-lookup"><span data-stu-id="e6c5d-106">Member</span></span>|<span data-ttu-id="e6c5d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e6c5d-107">Description</span></span>|  
|------------|-----------------|  
|`cbAssemblyInfo`|<span data-ttu-id="e6c5d-108">Velikost v bajtech, struktury.</span><span class="sxs-lookup"><span data-stu-id="e6c5d-108">The size, in bytes, of the structure.</span></span> <span data-ttu-id="e6c5d-109">Toto pole je vyhrazený pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="e6c5d-109">This field is reserved for future extensibility.</span></span>|  
|`dwAssemblyFlags`|<span data-ttu-id="e6c5d-110">Příznaky, které indikují instalace podrobnosti o sestavení.</span><span class="sxs-lookup"><span data-stu-id="e6c5d-110">Flags that indicate installation details about the assembly.</span></span> <span data-ttu-id="e6c5d-111">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="e6c5d-111">The following values are supported:</span></span><br /><br /> <span data-ttu-id="e6c5d-112">Hodnota-ASSEMBLYINFO_FLAG_INSTALLED, která označuje, že je nainstalován sestavení.</span><span class="sxs-lookup"><span data-stu-id="e6c5d-112">-   The ASSEMBLYINFO_FLAG_INSTALLED value, which indicates that the assembly is installed.</span></span> <span data-ttu-id="e6c5d-113">Aktuální verze rozhraní .NET Framework vždy nastaví `dwAssemblyFlags` na tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e6c5d-113">The current version of the .NET Framework always sets `dwAssemblyFlags` to this value.</span></span><br /><span data-ttu-id="e6c5d-114">Hodnota-ASSEMBLYINFO_FLAG_PAYLOADRESIDENT, která označuje, že je sestavení trvalé datové části.</span><span class="sxs-lookup"><span data-stu-id="e6c5d-114">-   The ASSEMBLYINFO_FLAG_PAYLOADRESIDENT value, which indicates that the assembly is a payload resident.</span></span> <span data-ttu-id="e6c5d-115">Aktuální verze rozhraní .NET Framework nikdy nastaví `dwAssemblyFlags` na tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e6c5d-115">The current version of the .NET Framework never sets `dwAssemblyFlags` to this value.</span></span>|  
|`uliAssemblySizeInKB`|<span data-ttu-id="e6c5d-116">Celková velikost v kilobajtech, soubory, které obsahuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="e6c5d-116">The total size, in kilobytes, of the files that the assembly contains.</span></span>|  
|`pszCurrentAssemblyPathBuf`|<span data-ttu-id="e6c5d-117">Ukazatel na řetězec vyrovnávací paměť, která obsahuje aktuální cestu k souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="e6c5d-117">A pointer to a string buffer that holds the current path to the manifest file.</span></span> <span data-ttu-id="e6c5d-118">Cesta musí končit znak hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="e6c5d-118">The path must end with a null character.</span></span>|  
|`cchBuf`|<span data-ttu-id="e6c5d-119">Počet široké znaky, včetně null ukončovací znak, který `pszCurrentAssemblyPathBuf` obsahuje.</span><span class="sxs-lookup"><span data-stu-id="e6c5d-119">The number of wide characters, including the null terminator, that `pszCurrentAssemblyPathBuf` contains.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e6c5d-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e6c5d-120">Requirements</span></span>  
 <span data-ttu-id="e6c5d-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6c5d-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6c5d-122">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="e6c5d-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e6c5d-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6c5d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6c5d-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6c5d-124">See Also</span></span>  
 [<span data-ttu-id="e6c5d-125">Struktury pro fúze</span><span class="sxs-lookup"><span data-stu-id="e6c5d-125">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
 [<span data-ttu-id="e6c5d-126">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="e6c5d-126">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
