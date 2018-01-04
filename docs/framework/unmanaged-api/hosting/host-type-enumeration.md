---
title: "HOST_TYPE – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: HOST_TYPE
api_location: mscoree.dll
api_type: COM
f1_keywords: HOST_TYPE
helpviewer_keywords: HOST_TYPE enumeration [.NET Framework hosting]
ms.assetid: 51f848be-84c5-4036-9839-c762c576bbf5
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8c910dd06109a8a69f29517812737d4b4dcef21
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="hosttype-enumeration"></a><span data-ttu-id="7b691-102">HOST_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="7b691-102">HOST_TYPE Enumeration</span></span>
<span data-ttu-id="7b691-103">Obsahuje hodnoty, které určují typ hostitele, který je spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="7b691-103">Contains values that specify the type of host that is launching an application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b691-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b691-104">Syntax</span></span>  
  
```  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="7b691-105">Členové</span><span class="sxs-lookup"><span data-stu-id="7b691-105">Members</span></span>  
  
|<span data-ttu-id="7b691-106">Člen</span><span class="sxs-lookup"><span data-stu-id="7b691-106">Member</span></span>|<span data-ttu-id="7b691-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7b691-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|<span data-ttu-id="7b691-108">Spusťte aplikaci z AppLaunch.exe.</span><span class="sxs-lookup"><span data-stu-id="7b691-108">Launch the application from AppLaunch.exe.</span></span><br /><br /> <span data-ttu-id="7b691-109">Tato hodnota se používá pro částečně důvěryhodné aplikace.</span><span class="sxs-lookup"><span data-stu-id="7b691-109">Use this value for partially-trusted applications.</span></span>|  
|`HOST_TYPE_CORFLAG`|<span data-ttu-id="7b691-110">Spuštění aplikace přímo.</span><span class="sxs-lookup"><span data-stu-id="7b691-110">Launch the application directly.</span></span> <span data-ttu-id="7b691-111">To znamená spusťte aplikaci z vlastního souboru .exe.</span><span class="sxs-lookup"><span data-stu-id="7b691-111">That is, launch the application from its own .exe file.</span></span><br /><br /> <span data-ttu-id="7b691-112">Tato hodnota se používá pro plně důvěryhodné aplikace.</span><span class="sxs-lookup"><span data-stu-id="7b691-112">Use this value for fully-trusted applications.</span></span>|  
|`HOST_TYPE_DEFAULT`|<span data-ttu-id="7b691-113">Stejné jako HOST_TYPE_APPLAUNCH.</span><span class="sxs-lookup"><span data-stu-id="7b691-113">Same as HOST_TYPE_APPLAUNCH.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7b691-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7b691-114">Requirements</span></span>  
 <span data-ttu-id="7b691-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b691-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b691-116">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7b691-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7b691-117">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7b691-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7b691-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b691-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b691-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b691-119">See Also</span></span>  
 [<span data-ttu-id="7b691-120">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="7b691-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
