---
title: CorDebugMappingResult – výčet
ms.date: 03/30/2017
api_name:
- CorDebugMappingResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMappingResult
helpviewer_keywords:
- CorDebugMappingResult enumeration [.NET Framework debugging]
ms.assetid: 701281dd-2936-45c8-a1f0-3bf7332b093b
topic_type:
- apiref
ms.openlocfilehash: 317dc2fe8403ae25949410423f1a28ad365caf6a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789312"
---
# <a name="cordebugmappingresult-enumeration"></a><span data-ttu-id="78be8-102">CorDebugMappingResult – výčet</span><span class="sxs-lookup"><span data-stu-id="78be8-102">CorDebugMappingResult Enumeration</span></span>
<span data-ttu-id="78be8-103">Poskytuje podrobné informace o tom, jak byla získána hodnota ukazatele na instrukce (IP).</span><span class="sxs-lookup"><span data-stu-id="78be8-103">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78be8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78be8-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugMappingResult {  
    MAPPING_PROLOG              = 0x1,  
    MAPPING_EPILOG              = 0x2,  
    MAPPING_NO_INFO             = 0x4,  
    MAPPING_UNMAPPED_ADDRESS    = 0x8,  
    MAPPING_EXACT               = 0x10,  
    MAPPING_APPROXIMATE         = 0x20,  
} CorDebugMappingResult;  
```  
  
## <a name="members"></a><span data-ttu-id="78be8-105">Členové</span><span class="sxs-lookup"><span data-stu-id="78be8-105">Members</span></span>  
  
|<span data-ttu-id="78be8-106">Člen</span><span class="sxs-lookup"><span data-stu-id="78be8-106">Member</span></span>|<span data-ttu-id="78be8-107">Popis</span><span class="sxs-lookup"><span data-stu-id="78be8-107">Description</span></span>|  
|------------|-----------------|  
|`MAPPING_PROLOG`|<span data-ttu-id="78be8-108">Nativní kód je v prologu, takže hodnota IP je 0.</span><span class="sxs-lookup"><span data-stu-id="78be8-108">The native code is in the prolog, so the value of the IP is 0.</span></span>|  
|`MAPPING_EPILOG`|<span data-ttu-id="78be8-109">Nativní kód je ve epilogu, takže hodnota IP je adresa poslední instrukce metody.</span><span class="sxs-lookup"><span data-stu-id="78be8-109">The native code is in an epilog, so the value of the IP is the address of the last instruction of the method.</span></span>|  
|`MAPPING_NO_INFO`|<span data-ttu-id="78be8-110">Pro metodu nejsou k dispozici žádné informace o mapování, takže hodnota IP je 0.</span><span class="sxs-lookup"><span data-stu-id="78be8-110">No mapping information is available for the method, so the value of the IP is 0.</span></span>|  
|`MAPPING_UNMAPPED_ADDRESS`|<span data-ttu-id="78be8-111">I když jsou pro metodu k dispozici informace o mapování, nemůže být aktuální adresa namapována na kód jazyka MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="78be8-111">Although there is mapping information for the method, the current address cannot be mapped to Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="78be8-112">Hodnota IP je 0.</span><span class="sxs-lookup"><span data-stu-id="78be8-112">The value of the IP is 0.</span></span>|  
|`MAPPING_EXACT`|<span data-ttu-id="78be8-113">Buď je metoda mapována přesně na kód jazyka MSIL, nebo byl rámec interpretován, takže hodnota IP je přesná.</span><span class="sxs-lookup"><span data-stu-id="78be8-113">Either the method maps exactly to MSIL code or the frame has been interpreted, so the value of the IP is accurate.</span></span>|  
|`MAPPING_APPROXIMATE`|<span data-ttu-id="78be8-114">Metoda byla úspěšně namapována, ale hodnota IP adresy může být přibližná.</span><span class="sxs-lookup"><span data-stu-id="78be8-114">The method was successfully mapped, but the value of the IP may be approximate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78be8-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="78be8-115">Remarks</span></span>  
 <span data-ttu-id="78be8-116">K získání hodnoty ukazatele na instrukci můžete použít metodu [ICorDebugILFrame:: getip –](icordebugilframe-getip-method.md) .</span><span class="sxs-lookup"><span data-stu-id="78be8-116">You can use the [ICorDebugILFrame::GetIP](icordebugilframe-getip-method.md) method to obtain the value of the instruction pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78be8-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="78be8-117">Requirements</span></span>  
 <span data-ttu-id="78be8-118">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78be8-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78be8-119">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="78be8-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78be8-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="78be8-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78be8-121">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78be8-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78be8-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="78be8-122">See also</span></span>

- [<span data-ttu-id="78be8-123">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="78be8-123">Debugging Enumerations</span></span>](debugging-enumerations.md)
