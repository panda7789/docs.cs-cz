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
ms.openlocfilehash: cc0cea10b4a209583fb7afb551a6b80d52ad7f62
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127031"
---
# <a name="host_type-enumeration"></a><span data-ttu-id="6f77c-102">HOST_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="6f77c-102">HOST_TYPE Enumeration</span></span>
<span data-ttu-id="6f77c-103">Obsahuje hodnoty, které určují typ hostitele, který spouští aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6f77c-103">Contains values that specify the type of host that is launching an application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f77c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f77c-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="6f77c-105">Členové</span><span class="sxs-lookup"><span data-stu-id="6f77c-105">Members</span></span>  
  
|<span data-ttu-id="6f77c-106">Člen</span><span class="sxs-lookup"><span data-stu-id="6f77c-106">Member</span></span>|<span data-ttu-id="6f77c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="6f77c-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|<span data-ttu-id="6f77c-108">Spusťte aplikaci z souboru applaunch. exe.</span><span class="sxs-lookup"><span data-stu-id="6f77c-108">Launch the application from AppLaunch.exe.</span></span><br /><br /> <span data-ttu-id="6f77c-109">Tuto hodnotu použijte pro částečně důvěryhodné aplikace.</span><span class="sxs-lookup"><span data-stu-id="6f77c-109">Use this value for partially-trusted applications.</span></span>|  
|`HOST_TYPE_CORFLAG`|<span data-ttu-id="6f77c-110">Spusťte aplikaci přímo.</span><span class="sxs-lookup"><span data-stu-id="6f77c-110">Launch the application directly.</span></span> <span data-ttu-id="6f77c-111">To znamená, že aplikaci spustíte z vlastního souboru. exe.</span><span class="sxs-lookup"><span data-stu-id="6f77c-111">That is, launch the application from its own .exe file.</span></span><br /><br /> <span data-ttu-id="6f77c-112">Tuto hodnotu použijte pro plně důvěryhodné aplikace.</span><span class="sxs-lookup"><span data-stu-id="6f77c-112">Use this value for fully-trusted applications.</span></span>|  
|`HOST_TYPE_DEFAULT`|<span data-ttu-id="6f77c-113">Stejné jako HOST_TYPE_APPLAUNCH.</span><span class="sxs-lookup"><span data-stu-id="6f77c-113">Same as HOST_TYPE_APPLAUNCH.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6f77c-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6f77c-114">Requirements</span></span>  
 <span data-ttu-id="6f77c-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f77c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f77c-116">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6f77c-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6f77c-117">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6f77c-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6f77c-118">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f77c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f77c-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6f77c-119">See also</span></span>

- [<span data-ttu-id="6f77c-120">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="6f77c-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
