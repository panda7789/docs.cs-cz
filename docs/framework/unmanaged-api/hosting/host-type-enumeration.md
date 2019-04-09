---
title: HOST_TYPE – výčet
ms.date: 03/30/2017
api_name:
- HOST_TYPE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- HOST_TYPE
helpviewer_keywords:
- HOST_TYPE enumeration [.NET Framework hosting]
ms.assetid: 51f848be-84c5-4036-9839-c762c576bbf5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dfb1cff3e95c5ff86d22913745b7d14982766b48
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175224"
---
# <a name="hosttype-enumeration"></a><span data-ttu-id="88d96-102">HOST_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="88d96-102">HOST_TYPE Enumeration</span></span>
<span data-ttu-id="88d96-103">Obsahuje hodnoty, které určují typ hostitele, který spouští aplikaci.</span><span class="sxs-lookup"><span data-stu-id="88d96-103">Contains values that specify the type of host that is launching an application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88d96-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88d96-104">Syntax</span></span>  
  
```  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="88d96-105">Členové</span><span class="sxs-lookup"><span data-stu-id="88d96-105">Members</span></span>  
  
|<span data-ttu-id="88d96-106">Člen</span><span class="sxs-lookup"><span data-stu-id="88d96-106">Member</span></span>|<span data-ttu-id="88d96-107">Popis</span><span class="sxs-lookup"><span data-stu-id="88d96-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|<span data-ttu-id="88d96-108">Spuštění aplikace z AppLaunch.exe.</span><span class="sxs-lookup"><span data-stu-id="88d96-108">Launch the application from AppLaunch.exe.</span></span><br /><br /> <span data-ttu-id="88d96-109">Používejte tuto hodnotu pro částečně důvěryhodné aplikace.</span><span class="sxs-lookup"><span data-stu-id="88d96-109">Use this value for partially-trusted applications.</span></span>|  
|`HOST_TYPE_CORFLAG`|<span data-ttu-id="88d96-110">Spusťte aplikaci přímo.</span><span class="sxs-lookup"><span data-stu-id="88d96-110">Launch the application directly.</span></span> <span data-ttu-id="88d96-111">To znamená spusťte aplikaci z vlastního souboru .exe.</span><span class="sxs-lookup"><span data-stu-id="88d96-111">That is, launch the application from its own .exe file.</span></span><br /><br /> <span data-ttu-id="88d96-112">Používejte tuto hodnotu pro plně důvěryhodné aplikace.</span><span class="sxs-lookup"><span data-stu-id="88d96-112">Use this value for fully-trusted applications.</span></span>|  
|`HOST_TYPE_DEFAULT`|<span data-ttu-id="88d96-113">Stejné jako HOST_TYPE_APPLAUNCH.</span><span class="sxs-lookup"><span data-stu-id="88d96-113">Same as HOST_TYPE_APPLAUNCH.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="88d96-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="88d96-114">Requirements</span></span>  
 <span data-ttu-id="88d96-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88d96-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88d96-116">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="88d96-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="88d96-117">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="88d96-117">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="88d96-118">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="88d96-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="88d96-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="88d96-119">See also</span></span>

- [<span data-ttu-id="88d96-120">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="88d96-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
