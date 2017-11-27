---
title: "ASSEMBLY_INFO – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ASSEMBLY_INFO
api_location: fusion.dll
api_type: COM
f1_keywords: ASSEMBLY_INFO
helpviewer_keywords: ASSEMBLY_INFO structure [.NET Framework fusion]
ms.assetid: b3cbb47c-457f-4083-8895-49562ca99ab8
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d532bbd2d338f942c09c4213620468a3361db5f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="assemblyinfo-structure"></a><span data-ttu-id="2998b-102">ASSEMBLY_INFO – struktura</span><span class="sxs-lookup"><span data-stu-id="2998b-102">ASSEMBLY_INFO Structure</span></span>
<span data-ttu-id="2998b-103">Obsahuje informace o sestavení, které je zaregistrován v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="2998b-103">Contains information about an assembly that is registered in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2998b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2998b-104">Syntax</span></span>  
  
```  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="2998b-105">Členové</span><span class="sxs-lookup"><span data-stu-id="2998b-105">Members</span></span>  
  
|<span data-ttu-id="2998b-106">Člen</span><span class="sxs-lookup"><span data-stu-id="2998b-106">Member</span></span>|<span data-ttu-id="2998b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2998b-107">Description</span></span>|  
|------------|-----------------|  
|`cbAssemblyInfo`|<span data-ttu-id="2998b-108">Velikost v bajtech, struktury.</span><span class="sxs-lookup"><span data-stu-id="2998b-108">The size, in bytes, of the structure.</span></span> <span data-ttu-id="2998b-109">Toto pole je vyhrazený pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="2998b-109">This field is reserved for future extensibility.</span></span>|  
|`dwAssemblyFlags`|<span data-ttu-id="2998b-110">Příznaky, které indikují instalace podrobnosti o sestavení.</span><span class="sxs-lookup"><span data-stu-id="2998b-110">Flags that indicate installation details about the assembly.</span></span> <span data-ttu-id="2998b-111">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="2998b-111">The following values are supported:</span></span><br /><br /> <span data-ttu-id="2998b-112">Hodnota-ASSEMBLYINFO_FLAG_INSTALLED, která označuje, že je nainstalován sestavení.</span><span class="sxs-lookup"><span data-stu-id="2998b-112">-   The ASSEMBLYINFO_FLAG_INSTALLED value, which indicates that the assembly is installed.</span></span> <span data-ttu-id="2998b-113">Aktuální verze rozhraní .NET Framework vždy nastaví `dwAssemblyFlags` na tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2998b-113">The current version of the .NET Framework always sets `dwAssemblyFlags` to this value.</span></span><br /><span data-ttu-id="2998b-114">Hodnota-ASSEMBLYINFO_FLAG_PAYLOADRESIDENT, která označuje, že je sestavení trvalé datové části.</span><span class="sxs-lookup"><span data-stu-id="2998b-114">-   The ASSEMBLYINFO_FLAG_PAYLOADRESIDENT value, which indicates that the assembly is a payload resident.</span></span> <span data-ttu-id="2998b-115">Aktuální verze rozhraní .NET Framework nikdy nastaví `dwAssemblyFlags` na tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2998b-115">The current version of the .NET Framework never sets `dwAssemblyFlags` to this value.</span></span>|  
|`uliAssemblySizeInKB`|<span data-ttu-id="2998b-116">Celková velikost v kilobajtech, soubory, které obsahuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="2998b-116">The total size, in kilobytes, of the files that the assembly contains.</span></span>|  
|`pszCurrentAssemblyPathBuf`|<span data-ttu-id="2998b-117">Ukazatel na řetězec vyrovnávací paměť, která obsahuje aktuální cestu k souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="2998b-117">A pointer to a string buffer that holds the current path to the manifest file.</span></span> <span data-ttu-id="2998b-118">Cesta musí končit znak hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="2998b-118">The path must end with a null character.</span></span>|  
|`cchBuf`|<span data-ttu-id="2998b-119">Počet široké znaky, včetně null ukončovací znak, který `pszCurrentAssemblyPathBuf` obsahuje.</span><span class="sxs-lookup"><span data-stu-id="2998b-119">The number of wide characters, including the null terminator, that `pszCurrentAssemblyPathBuf` contains.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2998b-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2998b-120">Requirements</span></span>  
 <span data-ttu-id="2998b-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2998b-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2998b-122">**Záhlaví:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="2998b-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="2998b-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2998b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2998b-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="2998b-124">See Also</span></span>  
 [<span data-ttu-id="2998b-125">Struktury fúzí</span><span class="sxs-lookup"><span data-stu-id="2998b-125">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
 [<span data-ttu-id="2998b-126">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="2998b-126">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
