---
title: "CorRegFlags – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorRegFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: CorRegFlags
helpviewer_keywords: CorRegFlags enumeration [.NET Framework metadata]
ms.assetid: 8d3080ee-39fe-4c57-8950-51323632d045
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5f2dcc60d41369250409cccf5b340e98f0cb4ca8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="7f009-102">CorRegFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="7f009-102">CorRegFlags Enumeration</span></span>
<span data-ttu-id="7f009-103">Poskytuje příznak hodnoty používané pro registraci, při instalaci modulu nebo složený bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="7f009-103">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f009-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f009-104">Syntax</span></span>  
  
```  
typedef enum   
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="7f009-105">Členové</span><span class="sxs-lookup"><span data-stu-id="7f009-105">Members</span></span>  
  
|<span data-ttu-id="7f009-106">Člen</span><span class="sxs-lookup"><span data-stu-id="7f009-106">Member</span></span>|<span data-ttu-id="7f009-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7f009-107">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="7f009-108">Určuje, že soubory by neměly být zkopírovány do cílové.</span><span class="sxs-lookup"><span data-stu-id="7f009-108">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="7f009-109">Určuje, že modulu nebo složené je konfigurace.</span><span class="sxs-lookup"><span data-stu-id="7f009-109">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="7f009-110">Určuje, že modulu nebo složené obsahuje odkazy na třídy.</span><span class="sxs-lookup"><span data-stu-id="7f009-110">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7f009-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7f009-111">Requirements</span></span>  
 <span data-ttu-id="7f009-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f009-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f009-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7f009-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7f009-114">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7f009-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7f009-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f009-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f009-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f009-116">See Also</span></span>  
 [<span data-ttu-id="7f009-117">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="7f009-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
