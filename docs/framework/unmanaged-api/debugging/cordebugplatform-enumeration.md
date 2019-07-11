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
ms.openlocfilehash: b8c0644dc247225c510e1c84254417551b490416
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739664"
---
# <a name="cordebugplatform-enumeration"></a><span data-ttu-id="4fc88-102">Výčet CorDebugPlatform</span><span class="sxs-lookup"><span data-stu-id="4fc88-102">CorDebugPlatform Enumeration</span></span>
<span data-ttu-id="4fc88-103">Poskytuje cílové platformy hodnoty, které jsou používány [icordebugdatatarget::getplatform –](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="4fc88-103">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fc88-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4fc88-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="4fc88-105">Členové</span><span class="sxs-lookup"><span data-stu-id="4fc88-105">Members</span></span>  
  
|<span data-ttu-id="4fc88-106">Člen</span><span class="sxs-lookup"><span data-stu-id="4fc88-106">Member</span></span>|<span data-ttu-id="4fc88-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4fc88-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4fc88-108">CORDB_PLATFORM_WINDOWS_X86</span><span class="sxs-lookup"><span data-stu-id="4fc88-108">CORDB_PLATFORM_WINDOWS_X86</span></span>|<span data-ttu-id="4fc88-109">Cílová platforma je hardware Intel x86 a systémem Windows.</span><span class="sxs-lookup"><span data-stu-id="4fc88-109">The target platform is Windows running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="4fc88-110">CORDB_PLATFORM_WINDOWS_AMD64</span><span class="sxs-lookup"><span data-stu-id="4fc88-110">CORDB_PLATFORM_WINDOWS_AMD64</span></span>|<span data-ttu-id="4fc88-111">Cílová platforma je 64bitová verze Windows běží na AMD64 nebo Intel EM64T hardwaru.</span><span class="sxs-lookup"><span data-stu-id="4fc88-111">The target platform is 64 bit Windows running on AMD64 or Intel EM64T hardware.</span></span>|  
|<span data-ttu-id="4fc88-112">CORDB_PLATFORM_WINDOWS_IA64</span><span class="sxs-lookup"><span data-stu-id="4fc88-112">CORDB_PLATFORM_WINDOWS_IA64</span></span>|<span data-ttu-id="4fc88-113">Cílová platforma je hardware Intel IA-64 a systémem Windows 32 bitů.</span><span class="sxs-lookup"><span data-stu-id="4fc88-113">The target platform is 32 bit Windows running on Intel IA-64 hardware.</span></span>|  
|<span data-ttu-id="4fc88-114">CORDB_PLATFORM_MAC_PPC</span><span class="sxs-lookup"><span data-stu-id="4fc88-114">CORDB_PLATFORM_MAC_PPC</span></span>|<span data-ttu-id="4fc88-115">Cílová platforma je operační systém Macintosh na PowerPC hardwaru.</span><span class="sxs-lookup"><span data-stu-id="4fc88-115">The target platform is the Macintosh operating system running on PowerPC hardware.</span></span>|  
|<span data-ttu-id="4fc88-116">CORDB_PLATFORM_MAC_X86</span><span class="sxs-lookup"><span data-stu-id="4fc88-116">CORDB_PLATFORM_MAC_X86</span></span>|<span data-ttu-id="4fc88-117">Cílová platforma je operační systém Macintosh na Intel x86 hardwaru.</span><span class="sxs-lookup"><span data-stu-id="4fc88-117">The target platform is the Macintosh operating system running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="4fc88-118">CORDB_PLATFORM_WINDOWS_ARM</span><span class="sxs-lookup"><span data-stu-id="4fc88-118">CORDB_PLATFORM_WINDOWS_ARM</span></span>|<span data-ttu-id="4fc88-119">Cílová platforma je operační systém Macintosh běžící na Windows ARM hardwaru.</span><span class="sxs-lookup"><span data-stu-id="4fc88-119">The target platform is the Macintosh operating system running on Windows ARM hardware.</span></span>|  
|<span data-ttu-id="4fc88-120">CORDB_PLATFORM_MAC_AMD64</span><span class="sxs-lookup"><span data-stu-id="4fc88-120">CORDB_PLATFORM_MAC_AMD64</span></span>|<span data-ttu-id="4fc88-121">Cílová platforma je operační systém Macintosh na hardwaru AMD64.</span><span class="sxs-lookup"><span data-stu-id="4fc88-121">The target platform is the Macintosh operating system running on AMD64 hardware.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4fc88-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4fc88-122">Requirements</span></span>  
 <span data-ttu-id="4fc88-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fc88-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fc88-124">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4fc88-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4fc88-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4fc88-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4fc88-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fc88-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
 <span data-ttu-id="4fc88-127">`CORDB_PLATFORM_WINDOWS_ARM` a `CORDB_PLATFORM_MAC_AMD64` členy jsou k dispozici v rozhraní .NET Framework 4.5.2 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="4fc88-127">The `CORDB_PLATFORM_WINDOWS_ARM` and `CORDB_PLATFORM_MAC_AMD64` members are available in the .NET Framework 4.5.2 and later versions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fc88-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4fc88-128">See also</span></span>

- [<span data-ttu-id="4fc88-129">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="4fc88-129">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
