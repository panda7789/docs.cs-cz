---
title: "RUNTIME_INFO_FLAGS – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: RUNTIME_INFO_FLAGS
api_location: mscoree.dll
api_type: COM
f1_keywords: RUNTIME_INFO_FLAGS
helpviewer_keywords: RUNTIME_INFO_FLAGS enumeration [.NET Framework hosting]
ms.assetid: adba37be-f775-4cdb-8919-5746ce694f33
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d050972857ba652ae0b40727260f681c383208b0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="runtimeinfoflags-enumeration"></a><span data-ttu-id="f836f-102">RUNTIME_INFO_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="f836f-102">RUNTIME_INFO_FLAGS Enumeration</span></span>
<span data-ttu-id="f836f-103">Obsahuje hodnoty, které označují, jaké informace o common language runtime (CLR) má být vrácen.</span><span class="sxs-lookup"><span data-stu-id="f836f-103">Contains values that indicate what information about the common language runtime (CLR) should be returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f836f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f836f-104">Syntax</span></span>  
  
```  
typedef enum {  
  
    RUNTIME_INFO_UPGRADE_VERSION             = 0x01,  
    RUNTIME_INFO_REQUEST_IA64                = 0x02,  
    RUNTIME_INFO_REQUEST_AMD64               = 0x04,  
    RUNTIME_INFO_REQUEST_X86                 = 0x08,  
    RUNTIME_INFO_DONT_RETURN_DIRECTORY       = 0x10,  
    RUNTIME_INFO_DONT_RETURN_VERSION         = 0x20,  
    RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG      = 0x40,  
    RUNTIME_INFO_IGNORE_ERROR_MODE           = 0x1000  
  
} RUNTIME_INFO_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="f836f-105">Členové</span><span class="sxs-lookup"><span data-stu-id="f836f-105">Members</span></span>  
  
|<span data-ttu-id="f836f-106">Člen</span><span class="sxs-lookup"><span data-stu-id="f836f-106">Member</span></span>|<span data-ttu-id="f836f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f836f-107">Description</span></span>|  
|------------|-----------------|  
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|<span data-ttu-id="f836f-108">Označuje, že informací v adresáři nesmí být zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="f836f-108">Indicates that directory information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|<span data-ttu-id="f836f-109">Označuje, že informace o verzi, neměl by zahrnovat.</span><span class="sxs-lookup"><span data-stu-id="f836f-109">Indicates that version information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|<span data-ttu-id="f836f-110">Označuje, že by neměla zobrazit dialogové okno chyby při selhání.</span><span class="sxs-lookup"><span data-stu-id="f836f-110">Indicates that an error dialog box should not be shown upon failure.</span></span>|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|<span data-ttu-id="f836f-111">Určuje, že důsledky volání [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242) funkce s příznakem SEM_FAILCRITICALERRORS by měla být potlačena.</span><span class="sxs-lookup"><span data-stu-id="f836f-111">Indicates that the effects of calling the [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242) function with the SEM_FAILCRITICALERRORS flag should be overridden.</span></span> <span data-ttu-id="f836f-112">To znamená dialogové okno instalace se mají při selhání, místo potlačeny.</span><span class="sxs-lookup"><span data-stu-id="f836f-112">That is, an installation dialog box should be shown upon failure, instead of being suppressed.</span></span>|  
|`RUNTIME_INFO_REQUEST_AMD64`|<span data-ttu-id="f836f-113">Určuje žádost o informace o AMD-64-compatible verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="f836f-113">Indicates a request for information about an AMD-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_IA64`|<span data-ttu-id="f836f-114">Určuje žádost o informace o IA-64-compatible verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="f836f-114">Indicates a request for information about an IA-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_X86`|<span data-ttu-id="f836f-115">Určuje žádost o informace o x86 kompatibilní verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="f836f-115">Indicates a request for information about an x86-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_UPGRADE_VERSION`|<span data-ttu-id="f836f-116">Označuje, že informace o upgradu verze by měly být zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="f836f-116">Indicates that version upgrade information should be included.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f836f-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f836f-117">Remarks</span></span>  
 <span data-ttu-id="f836f-118">Následující příznaky Architektura platformy může být zadaná jenom jedna najednou a nelze jej kombinovat:</span><span class="sxs-lookup"><span data-stu-id="f836f-118">The following platform architecture flags can be specified only one at a time and cannot be combined:</span></span>  
  
-   <span data-ttu-id="f836f-119">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="f836f-119">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
-   <span data-ttu-id="f836f-120">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="f836f-120">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
-   <span data-ttu-id="f836f-121">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="f836f-121">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f836f-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f836f-122">Requirements</span></span>  
 <span data-ttu-id="f836f-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f836f-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f836f-124">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f836f-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f836f-125">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f836f-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f836f-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f836f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f836f-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="f836f-127">See Also</span></span>  
 [<span data-ttu-id="f836f-128">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="f836f-128">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
