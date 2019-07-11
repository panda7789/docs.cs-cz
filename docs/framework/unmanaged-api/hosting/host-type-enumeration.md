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
ms.openlocfilehash: caf76fa7962de9392b06591777ac862aa548d20d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779553"
---
# <a name="hosttype-enumeration"></a><span data-ttu-id="1e689-102">HOST_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="1e689-102">HOST_TYPE Enumeration</span></span>
<span data-ttu-id="1e689-103">Obsahuje hodnoty, které určují typ hostitele, který spouští aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1e689-103">Contains values that specify the type of host that is launching an application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e689-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e689-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="1e689-105">Členové</span><span class="sxs-lookup"><span data-stu-id="1e689-105">Members</span></span>  
  
|<span data-ttu-id="1e689-106">Člen</span><span class="sxs-lookup"><span data-stu-id="1e689-106">Member</span></span>|<span data-ttu-id="1e689-107">Popis</span><span class="sxs-lookup"><span data-stu-id="1e689-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|<span data-ttu-id="1e689-108">Spuštění aplikace z AppLaunch.exe.</span><span class="sxs-lookup"><span data-stu-id="1e689-108">Launch the application from AppLaunch.exe.</span></span><br /><br /> <span data-ttu-id="1e689-109">Používejte tuto hodnotu pro částečně důvěryhodné aplikace.</span><span class="sxs-lookup"><span data-stu-id="1e689-109">Use this value for partially-trusted applications.</span></span>|  
|`HOST_TYPE_CORFLAG`|<span data-ttu-id="1e689-110">Spusťte aplikaci přímo.</span><span class="sxs-lookup"><span data-stu-id="1e689-110">Launch the application directly.</span></span> <span data-ttu-id="1e689-111">To znamená spusťte aplikaci z vlastního souboru .exe.</span><span class="sxs-lookup"><span data-stu-id="1e689-111">That is, launch the application from its own .exe file.</span></span><br /><br /> <span data-ttu-id="1e689-112">Používejte tuto hodnotu pro plně důvěryhodné aplikace.</span><span class="sxs-lookup"><span data-stu-id="1e689-112">Use this value for fully-trusted applications.</span></span>|  
|`HOST_TYPE_DEFAULT`|<span data-ttu-id="1e689-113">Stejné jako HOST_TYPE_APPLAUNCH.</span><span class="sxs-lookup"><span data-stu-id="1e689-113">Same as HOST_TYPE_APPLAUNCH.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1e689-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1e689-114">Requirements</span></span>  
 <span data-ttu-id="1e689-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e689-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e689-116">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1e689-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1e689-117">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1e689-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1e689-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e689-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e689-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1e689-119">See also</span></span>

- [<span data-ttu-id="1e689-120">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="1e689-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
