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
ms.openlocfilehash: fce759877ad5e3c9041344647781da07ad19a45a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430891"
---
# <a name="hosttype-enumeration"></a><span data-ttu-id="5425c-102">HOST_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="5425c-102">HOST_TYPE Enumeration</span></span>
<span data-ttu-id="5425c-103">Obsahuje hodnoty, které určují typ hostitele, který je spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="5425c-103">Contains values that specify the type of host that is launching an application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5425c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5425c-104">Syntax</span></span>  
  
```  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="5425c-105">Členové</span><span class="sxs-lookup"><span data-stu-id="5425c-105">Members</span></span>  
  
|<span data-ttu-id="5425c-106">Člen</span><span class="sxs-lookup"><span data-stu-id="5425c-106">Member</span></span>|<span data-ttu-id="5425c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="5425c-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|<span data-ttu-id="5425c-108">Spusťte aplikaci z AppLaunch.exe.</span><span class="sxs-lookup"><span data-stu-id="5425c-108">Launch the application from AppLaunch.exe.</span></span><br /><br /> <span data-ttu-id="5425c-109">Tato hodnota se používá pro částečně důvěryhodné aplikace.</span><span class="sxs-lookup"><span data-stu-id="5425c-109">Use this value for partially-trusted applications.</span></span>|  
|`HOST_TYPE_CORFLAG`|<span data-ttu-id="5425c-110">Spuštění aplikace přímo.</span><span class="sxs-lookup"><span data-stu-id="5425c-110">Launch the application directly.</span></span> <span data-ttu-id="5425c-111">To znamená spusťte aplikaci z vlastního souboru .exe.</span><span class="sxs-lookup"><span data-stu-id="5425c-111">That is, launch the application from its own .exe file.</span></span><br /><br /> <span data-ttu-id="5425c-112">Tato hodnota se používá pro plně důvěryhodné aplikace.</span><span class="sxs-lookup"><span data-stu-id="5425c-112">Use this value for fully-trusted applications.</span></span>|  
|`HOST_TYPE_DEFAULT`|<span data-ttu-id="5425c-113">Stejné jako HOST_TYPE_APPLAUNCH.</span><span class="sxs-lookup"><span data-stu-id="5425c-113">Same as HOST_TYPE_APPLAUNCH.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5425c-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5425c-114">Requirements</span></span>  
 <span data-ttu-id="5425c-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5425c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5425c-116">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5425c-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5425c-117">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5425c-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5425c-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5425c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5425c-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="5425c-119">See Also</span></span>  
 [<span data-ttu-id="5425c-120">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="5425c-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
