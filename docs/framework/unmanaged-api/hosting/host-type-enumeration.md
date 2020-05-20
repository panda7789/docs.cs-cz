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
ms.openlocfilehash: e8dda83df8a320733f45dbcc13599cdf37d26492
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617149"
---
# <a name="host_type-enumeration"></a><span data-ttu-id="91c96-102">HOST_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="91c96-102">HOST_TYPE Enumeration</span></span>
<span data-ttu-id="91c96-103">Obsahuje hodnoty, které určují typ hostitele, který spouští aplikaci.</span><span class="sxs-lookup"><span data-stu-id="91c96-103">Contains values that specify the type of host that is launching an application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91c96-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91c96-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="91c96-105">Členové</span><span class="sxs-lookup"><span data-stu-id="91c96-105">Members</span></span>  
  
|<span data-ttu-id="91c96-106">Člen</span><span class="sxs-lookup"><span data-stu-id="91c96-106">Member</span></span>|<span data-ttu-id="91c96-107">Popis</span><span class="sxs-lookup"><span data-stu-id="91c96-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|<span data-ttu-id="91c96-108">Spusťte aplikaci z souboru applaunch. exe.</span><span class="sxs-lookup"><span data-stu-id="91c96-108">Launch the application from AppLaunch.exe.</span></span><br /><br /> <span data-ttu-id="91c96-109">Tuto hodnotu použijte pro částečně důvěryhodné aplikace.</span><span class="sxs-lookup"><span data-stu-id="91c96-109">Use this value for partially-trusted applications.</span></span>|  
|`HOST_TYPE_CORFLAG`|<span data-ttu-id="91c96-110">Spusťte aplikaci přímo.</span><span class="sxs-lookup"><span data-stu-id="91c96-110">Launch the application directly.</span></span> <span data-ttu-id="91c96-111">To znamená, že aplikaci spustíte z vlastního souboru. exe.</span><span class="sxs-lookup"><span data-stu-id="91c96-111">That is, launch the application from its own .exe file.</span></span><br /><br /> <span data-ttu-id="91c96-112">Tuto hodnotu použijte pro plně důvěryhodné aplikace.</span><span class="sxs-lookup"><span data-stu-id="91c96-112">Use this value for fully-trusted applications.</span></span>|  
|`HOST_TYPE_DEFAULT`|<span data-ttu-id="91c96-113">Stejné jako HOST_TYPE_APPLAUNCH.</span><span class="sxs-lookup"><span data-stu-id="91c96-113">Same as HOST_TYPE_APPLAUNCH.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="91c96-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="91c96-114">Requirements</span></span>  
 <span data-ttu-id="91c96-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91c96-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91c96-116">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="91c96-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="91c96-117">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="91c96-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="91c96-118">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91c96-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91c96-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="91c96-119">See also</span></span>

- [<span data-ttu-id="91c96-120">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="91c96-120">Hosting Enumerations</span></span>](hosting-enumerations.md)
