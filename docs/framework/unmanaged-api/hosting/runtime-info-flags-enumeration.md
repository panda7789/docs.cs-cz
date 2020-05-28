---
title: RUNTIME_INFO_FLAGS – výčet
ms.date: 03/30/2017
api_name:
- RUNTIME_INFO_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RUNTIME_INFO_FLAGS
helpviewer_keywords:
- RUNTIME_INFO_FLAGS enumeration [.NET Framework hosting]
ms.assetid: adba37be-f775-4cdb-8919-5746ce694f33
topic_type:
- apiref
ms.openlocfilehash: da830aaaced179fed642340c33e7b7c37b350aa3
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006555"
---
# <a name="runtime_info_flags-enumeration"></a><span data-ttu-id="b26e0-102">RUNTIME_INFO_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="b26e0-102">RUNTIME_INFO_FLAGS Enumeration</span></span>
<span data-ttu-id="b26e0-103">Obsahuje hodnoty, které určují, jaké informace o modulu CLR (Common Language Runtime) by měly být vráceny.</span><span class="sxs-lookup"><span data-stu-id="b26e0-103">Contains values that indicate what information about the common language runtime (CLR) should be returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b26e0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b26e0-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="b26e0-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b26e0-105">Members</span></span>  
  
|<span data-ttu-id="b26e0-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b26e0-106">Member</span></span>|<span data-ttu-id="b26e0-107">Description</span><span class="sxs-lookup"><span data-stu-id="b26e0-107">Description</span></span>|  
|------------|-----------------|  
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|<span data-ttu-id="b26e0-108">Označuje, že by neměly být zahrnuty informace o adresáři.</span><span class="sxs-lookup"><span data-stu-id="b26e0-108">Indicates that directory information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|<span data-ttu-id="b26e0-109">Určuje, že by neměly být zahrnuty informace o verzi.</span><span class="sxs-lookup"><span data-stu-id="b26e0-109">Indicates that version information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|<span data-ttu-id="b26e0-110">Označuje, že při selhání by se nemělo zobrazovat dialogové okno s chybou.</span><span class="sxs-lookup"><span data-stu-id="b26e0-110">Indicates that an error dialog box should not be shown upon failure.</span></span>|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|<span data-ttu-id="b26e0-111">Označuje, že účinky volání funkce [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) s příznakem SEM_FAILCRITICALERRORS by měly být přepsány.</span><span class="sxs-lookup"><span data-stu-id="b26e0-111">Indicates that the effects of calling the [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) function with the SEM_FAILCRITICALERRORS flag should be overridden.</span></span> <span data-ttu-id="b26e0-112">To znamená, že při selhání by se mělo zobrazit dialogové okno instalace, místo aby se potlačilo.</span><span class="sxs-lookup"><span data-stu-id="b26e0-112">That is, an installation dialog box should be shown upon failure, instead of being suppressed.</span></span>|  
|`RUNTIME_INFO_REQUEST_AMD64`|<span data-ttu-id="b26e0-113">Označuje požadavek na informace o verzi modulu runtime kompatibilní s technologií AMD-64.</span><span class="sxs-lookup"><span data-stu-id="b26e0-113">Indicates a request for information about an AMD-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_IA64`|<span data-ttu-id="b26e0-114">Označuje požadavek na informace o verzi modulu runtime kompatibilního s rozhraním IA-64.</span><span class="sxs-lookup"><span data-stu-id="b26e0-114">Indicates a request for information about an IA-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_X86`|<span data-ttu-id="b26e0-115">Označuje požadavek na informace o verzi modulu runtime kompatibilní s platformou x86.</span><span class="sxs-lookup"><span data-stu-id="b26e0-115">Indicates a request for information about an x86-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_UPGRADE_VERSION`|<span data-ttu-id="b26e0-116">Označuje, že by měly být zahrnuté informace o upgradu verze.</span><span class="sxs-lookup"><span data-stu-id="b26e0-116">Indicates that version upgrade information should be included.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b26e0-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b26e0-117">Remarks</span></span>  
 <span data-ttu-id="b26e0-118">Následující příznaky architektury platformy lze zadat pouze jednou a nelze je kombinovat:</span><span class="sxs-lookup"><span data-stu-id="b26e0-118">The following platform architecture flags can be specified only one at a time and cannot be combined:</span></span>  
  
- <span data-ttu-id="b26e0-119">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="b26e0-119">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
- <span data-ttu-id="b26e0-120">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="b26e0-120">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
- <span data-ttu-id="b26e0-121">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="b26e0-121">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b26e0-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b26e0-122">Requirements</span></span>  
 <span data-ttu-id="b26e0-123">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b26e0-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b26e0-124">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b26e0-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b26e0-125">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b26e0-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b26e0-126">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b26e0-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b26e0-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="b26e0-127">See also</span></span>

- [<span data-ttu-id="b26e0-128">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="b26e0-128">Hosting Enumerations</span></span>](hosting-enumerations.md)
