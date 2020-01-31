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
ms.openlocfilehash: 2ed32449c4a133e6e72ec44f9cb57f49de22164a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778234"
---
# <a name="cordebugplatform-enumeration"></a><span data-ttu-id="32ccf-102">Výčet CorDebugPlatform</span><span class="sxs-lookup"><span data-stu-id="32ccf-102">CorDebugPlatform Enumeration</span></span>
<span data-ttu-id="32ccf-103">Poskytuje hodnoty cílové platformy, které jsou používány metodou [ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) .</span><span class="sxs-lookup"><span data-stu-id="32ccf-103">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32ccf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32ccf-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="32ccf-105">Členové</span><span class="sxs-lookup"><span data-stu-id="32ccf-105">Members</span></span>  
  
|<span data-ttu-id="32ccf-106">Člen</span><span class="sxs-lookup"><span data-stu-id="32ccf-106">Member</span></span>|<span data-ttu-id="32ccf-107">Popis</span><span class="sxs-lookup"><span data-stu-id="32ccf-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="32ccf-108">CORDB_PLATFORM_WINDOWS_X86</span><span class="sxs-lookup"><span data-stu-id="32ccf-108">CORDB_PLATFORM_WINDOWS_X86</span></span>|<span data-ttu-id="32ccf-109">Cílová platforma je systémem Windows spuštěná na hardwaru Intel x86.</span><span class="sxs-lookup"><span data-stu-id="32ccf-109">The target platform is Windows running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="32ccf-110">CORDB_PLATFORM_WINDOWS_AMD64</span><span class="sxs-lookup"><span data-stu-id="32ccf-110">CORDB_PLATFORM_WINDOWS_AMD64</span></span>|<span data-ttu-id="32ccf-111">Cílová platforma je 64 bitových oken běžících na hardwaru AMD64 nebo Intel EM64T.</span><span class="sxs-lookup"><span data-stu-id="32ccf-111">The target platform is 64 bit Windows running on AMD64 or Intel EM64T hardware.</span></span>|  
|<span data-ttu-id="32ccf-112">CORDB_PLATFORM_WINDOWS_IA64</span><span class="sxs-lookup"><span data-stu-id="32ccf-112">CORDB_PLATFORM_WINDOWS_IA64</span></span>|<span data-ttu-id="32ccf-113">Cílová platforma je 32 bitových oken běžících na hardwaru Intel IA-64.</span><span class="sxs-lookup"><span data-stu-id="32ccf-113">The target platform is 32 bit Windows running on Intel IA-64 hardware.</span></span>|  
|<span data-ttu-id="32ccf-114">CORDB_PLATFORM_MAC_PPC</span><span class="sxs-lookup"><span data-stu-id="32ccf-114">CORDB_PLATFORM_MAC_PPC</span></span>|<span data-ttu-id="32ccf-115">Cílová platforma je operační systém Macintosh běžící na hardwaru PowerPC.</span><span class="sxs-lookup"><span data-stu-id="32ccf-115">The target platform is the Macintosh operating system running on PowerPC hardware.</span></span>|  
|<span data-ttu-id="32ccf-116">CORDB_PLATFORM_MAC_X86</span><span class="sxs-lookup"><span data-stu-id="32ccf-116">CORDB_PLATFORM_MAC_X86</span></span>|<span data-ttu-id="32ccf-117">Cílová platforma je operační systém Macintosh běžící na hardwaru Intel x86.</span><span class="sxs-lookup"><span data-stu-id="32ccf-117">The target platform is the Macintosh operating system running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="32ccf-118">CORDB_PLATFORM_WINDOWS_ARM</span><span class="sxs-lookup"><span data-stu-id="32ccf-118">CORDB_PLATFORM_WINDOWS_ARM</span></span>|<span data-ttu-id="32ccf-119">Cílová platforma je operační systém Macintosh běžící na hardwaru Windows ARM.</span><span class="sxs-lookup"><span data-stu-id="32ccf-119">The target platform is the Macintosh operating system running on Windows ARM hardware.</span></span>|  
|<span data-ttu-id="32ccf-120">CORDB_PLATFORM_MAC_AMD64</span><span class="sxs-lookup"><span data-stu-id="32ccf-120">CORDB_PLATFORM_MAC_AMD64</span></span>|<span data-ttu-id="32ccf-121">Cílová platforma je operační systém Macintosh běžící na hardwaru AMD64.</span><span class="sxs-lookup"><span data-stu-id="32ccf-121">The target platform is the Macintosh operating system running on AMD64 hardware.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="32ccf-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="32ccf-122">Requirements</span></span>  
 <span data-ttu-id="32ccf-123">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32ccf-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32ccf-124">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="32ccf-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32ccf-125">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="32ccf-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32ccf-126">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32ccf-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
 <span data-ttu-id="32ccf-127">Členové `CORDB_PLATFORM_WINDOWS_ARM` a `CORDB_PLATFORM_MAC_AMD64` jsou k dispozici v .NET Framework 4.5.2 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="32ccf-127">The `CORDB_PLATFORM_WINDOWS_ARM` and `CORDB_PLATFORM_MAC_AMD64` members are available in the .NET Framework 4.5.2 and later versions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32ccf-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="32ccf-128">See also</span></span>

- [<span data-ttu-id="32ccf-129">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="32ccf-129">Debugging Enumerations</span></span>](debugging-enumerations.md)
