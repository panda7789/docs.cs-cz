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
ms.openlocfilehash: 5d66503487e1b997e2b8cc7d3d46e210a4dbbe05
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132754"
---
# <a name="cordebugplatform-enumeration"></a><span data-ttu-id="7d724-102">Výčet CorDebugPlatform</span><span class="sxs-lookup"><span data-stu-id="7d724-102">CorDebugPlatform Enumeration</span></span>
<span data-ttu-id="7d724-103">Poskytuje hodnoty cílové platformy, které jsou používány metodou [ICorDebugDataTarget:: GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7d724-103">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d724-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d724-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="7d724-105">Členové</span><span class="sxs-lookup"><span data-stu-id="7d724-105">Members</span></span>  
  
|<span data-ttu-id="7d724-106">Člen</span><span class="sxs-lookup"><span data-stu-id="7d724-106">Member</span></span>|<span data-ttu-id="7d724-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7d724-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="7d724-108">CORDB_PLATFORM_WINDOWS_X86</span><span class="sxs-lookup"><span data-stu-id="7d724-108">CORDB_PLATFORM_WINDOWS_X86</span></span>|<span data-ttu-id="7d724-109">Cílová platforma je systémem Windows spuštěná na hardwaru Intel x86.</span><span class="sxs-lookup"><span data-stu-id="7d724-109">The target platform is Windows running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="7d724-110">CORDB_PLATFORM_WINDOWS_AMD64</span><span class="sxs-lookup"><span data-stu-id="7d724-110">CORDB_PLATFORM_WINDOWS_AMD64</span></span>|<span data-ttu-id="7d724-111">Cílová platforma je 64 bitových oken běžících na hardwaru AMD64 nebo Intel EM64T.</span><span class="sxs-lookup"><span data-stu-id="7d724-111">The target platform is 64 bit Windows running on AMD64 or Intel EM64T hardware.</span></span>|  
|<span data-ttu-id="7d724-112">CORDB_PLATFORM_WINDOWS_IA64</span><span class="sxs-lookup"><span data-stu-id="7d724-112">CORDB_PLATFORM_WINDOWS_IA64</span></span>|<span data-ttu-id="7d724-113">Cílová platforma je 32 bitových oken běžících na hardwaru Intel IA-64.</span><span class="sxs-lookup"><span data-stu-id="7d724-113">The target platform is 32 bit Windows running on Intel IA-64 hardware.</span></span>|  
|<span data-ttu-id="7d724-114">CORDB_PLATFORM_MAC_PPC</span><span class="sxs-lookup"><span data-stu-id="7d724-114">CORDB_PLATFORM_MAC_PPC</span></span>|<span data-ttu-id="7d724-115">Cílová platforma je operační systém Macintosh běžící na hardwaru PowerPC.</span><span class="sxs-lookup"><span data-stu-id="7d724-115">The target platform is the Macintosh operating system running on PowerPC hardware.</span></span>|  
|<span data-ttu-id="7d724-116">CORDB_PLATFORM_MAC_X86</span><span class="sxs-lookup"><span data-stu-id="7d724-116">CORDB_PLATFORM_MAC_X86</span></span>|<span data-ttu-id="7d724-117">Cílová platforma je operační systém Macintosh běžící na hardwaru Intel x86.</span><span class="sxs-lookup"><span data-stu-id="7d724-117">The target platform is the Macintosh operating system running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="7d724-118">CORDB_PLATFORM_WINDOWS_ARM</span><span class="sxs-lookup"><span data-stu-id="7d724-118">CORDB_PLATFORM_WINDOWS_ARM</span></span>|<span data-ttu-id="7d724-119">Cílová platforma je operační systém Macintosh běžící na hardwaru Windows ARM.</span><span class="sxs-lookup"><span data-stu-id="7d724-119">The target platform is the Macintosh operating system running on Windows ARM hardware.</span></span>|  
|<span data-ttu-id="7d724-120">CORDB_PLATFORM_MAC_AMD64</span><span class="sxs-lookup"><span data-stu-id="7d724-120">CORDB_PLATFORM_MAC_AMD64</span></span>|<span data-ttu-id="7d724-121">Cílová platforma je operační systém Macintosh běžící na hardwaru AMD64.</span><span class="sxs-lookup"><span data-stu-id="7d724-121">The target platform is the Macintosh operating system running on AMD64 hardware.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7d724-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d724-122">Requirements</span></span>  
 <span data-ttu-id="7d724-123">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d724-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d724-124">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7d724-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d724-125">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7d724-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d724-126">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d724-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
 <span data-ttu-id="7d724-127">Členové `CORDB_PLATFORM_WINDOWS_ARM` a `CORDB_PLATFORM_MAC_AMD64` jsou k dispozici v .NET Framework 4.5.2 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="7d724-127">The `CORDB_PLATFORM_WINDOWS_ARM` and `CORDB_PLATFORM_MAC_AMD64` members are available in the .NET Framework 4.5.2 and later versions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d724-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d724-128">See also</span></span>

- [<span data-ttu-id="7d724-129">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="7d724-129">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
