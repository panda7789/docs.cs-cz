---
title: Výčet CorDebugPlatform
ms.date: 03/30/2017
api_name:
- CorDebugPlatformEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugPlatformEnum
helpviewer_keywords:
- CorDebugPlatformEnum enumeration [.NET Framework debugging]
ms.assetid: c5444816-7378-4521-afd3-bf5e4b5303d5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03b6f1b29157889d0e84e5dddc94d5e3ae27efce
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180934"
---
# <a name="cordebugplatform-enumeration"></a><span data-ttu-id="8040d-102">Výčet CorDebugPlatform</span><span class="sxs-lookup"><span data-stu-id="8040d-102">CorDebugPlatform Enumeration</span></span>
<span data-ttu-id="8040d-103">Poskytuje cílové platformy hodnoty, které jsou používány [icordebugdatatarget::getplatform –](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="8040d-103">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8040d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8040d-104">Syntax</span></span>  
  
```  
typedef enum CorDebugPlatform  
{  
    CORDB_PLATFORM_WINDOWS_X86,    // Windows on Intel x86  
    CORDB_PLATFORM_WINDOWS_AMD64,  // Windows x64 (AMD64, Intel EM64T)  
    CORDB_PLATFORM_WINDOWS_IA64,   // Windows on Intel IA-64  
    CORDB_PLATFORM_MAC_PPC,        // Macintosh OS on PowerPC  
    CORDB_PLATFORM_MAC_X86,        // Macintosh OS on Intel x86  
    CORDB_PLATFORM_WINDOWS_ARM,    // Windows on ARM  
    CORDB_PLATFORM_MAC_AMD64       // MacOS on Intel x64  
} CorDebugPlatform;  
```  
  
## <a name="members"></a><span data-ttu-id="8040d-105">Členové</span><span class="sxs-lookup"><span data-stu-id="8040d-105">Members</span></span>  
  
|<span data-ttu-id="8040d-106">Člen</span><span class="sxs-lookup"><span data-stu-id="8040d-106">Member</span></span>|<span data-ttu-id="8040d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8040d-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="8040d-108">CORDB_PLATFORM_WINDOWS_X86</span><span class="sxs-lookup"><span data-stu-id="8040d-108">CORDB_PLATFORM_WINDOWS_X86</span></span>|<span data-ttu-id="8040d-109">Cílová platforma je hardware Intel x86 a systémem Windows.</span><span class="sxs-lookup"><span data-stu-id="8040d-109">The target platform is Windows running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="8040d-110">CORDB_PLATFORM_WINDOWS_AMD64</span><span class="sxs-lookup"><span data-stu-id="8040d-110">CORDB_PLATFORM_WINDOWS_AMD64</span></span>|<span data-ttu-id="8040d-111">Cílová platforma je 64bitová verze Windows běží na AMD64 nebo Intel EM64T hardwaru.</span><span class="sxs-lookup"><span data-stu-id="8040d-111">The target platform is 64 bit Windows running on AMD64 or Intel EM64T hardware.</span></span>|  
|<span data-ttu-id="8040d-112">CORDB_PLATFORM_WINDOWS_IA64</span><span class="sxs-lookup"><span data-stu-id="8040d-112">CORDB_PLATFORM_WINDOWS_IA64</span></span>|<span data-ttu-id="8040d-113">Cílová platforma je hardware Intel IA-64 a systémem Windows 32 bitů.</span><span class="sxs-lookup"><span data-stu-id="8040d-113">The target platform is 32 bit Windows running on Intel IA-64 hardware.</span></span>|  
|<span data-ttu-id="8040d-114">CORDB_PLATFORM_MAC_PPC</span><span class="sxs-lookup"><span data-stu-id="8040d-114">CORDB_PLATFORM_MAC_PPC</span></span>|<span data-ttu-id="8040d-115">Cílová platforma je operační systém Macintosh na PowerPC hardwaru.</span><span class="sxs-lookup"><span data-stu-id="8040d-115">The target platform is the Macintosh operating system running on PowerPC hardware.</span></span>|  
|<span data-ttu-id="8040d-116">CORDB_PLATFORM_MAC_X86</span><span class="sxs-lookup"><span data-stu-id="8040d-116">CORDB_PLATFORM_MAC_X86</span></span>|<span data-ttu-id="8040d-117">Cílová platforma je operační systém Macintosh na Intel x86 hardwaru.</span><span class="sxs-lookup"><span data-stu-id="8040d-117">The target platform is the Macintosh operating system running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="8040d-118">CORDB_PLATFORM_WINDOWS_ARM</span><span class="sxs-lookup"><span data-stu-id="8040d-118">CORDB_PLATFORM_WINDOWS_ARM</span></span>|<span data-ttu-id="8040d-119">Cílová platforma je operační systém Macintosh běžící na Windows ARM hardwaru.</span><span class="sxs-lookup"><span data-stu-id="8040d-119">The target platform is the Macintosh operating system running on Windows ARM hardware.</span></span>|  
|<span data-ttu-id="8040d-120">CORDB_PLATFORM_MAC_AMD64</span><span class="sxs-lookup"><span data-stu-id="8040d-120">CORDB_PLATFORM_MAC_AMD64</span></span>|<span data-ttu-id="8040d-121">Cílová platforma je operační systém Macintosh na hardwaru AMD64.</span><span class="sxs-lookup"><span data-stu-id="8040d-121">The target platform is the Macintosh operating system running on AMD64 hardware.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8040d-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8040d-122">Requirements</span></span>  
 <span data-ttu-id="8040d-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8040d-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8040d-124">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8040d-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8040d-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8040d-125">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="8040d-126">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="8040d-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
 <span data-ttu-id="8040d-127">`CORDB_PLATFORM_WINDOWS_ARM` a `CORDB_PLATFORM_MAC_AMD64` členy jsou k dispozici v rozhraní .NET Framework 4.5.2 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="8040d-127">The `CORDB_PLATFORM_WINDOWS_ARM` and `CORDB_PLATFORM_MAC_AMD64` members are available in the .NET Framework 4.5.2 and later versions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8040d-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8040d-128">See also</span></span>

- [<span data-ttu-id="8040d-129">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="8040d-129">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
