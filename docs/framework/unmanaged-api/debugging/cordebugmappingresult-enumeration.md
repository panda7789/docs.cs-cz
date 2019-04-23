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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c2fecc7160cb41e31bf88f1a461265ad8fdce166
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59170388"
---
# <a name="cordebugmappingresult-enumeration"></a><span data-ttu-id="c17c1-102">CorDebugMappingResult – výčet</span><span class="sxs-lookup"><span data-stu-id="c17c1-102">CorDebugMappingResult Enumeration</span></span>
<span data-ttu-id="c17c1-103">Poskytuje podrobnosti o způsobu získání hodnoty ukazatel instrukce (IP).</span><span class="sxs-lookup"><span data-stu-id="c17c1-103">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c17c1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c17c1-104">Syntax</span></span>  
  
```  
typedef enum CorDebugMappingResult {  
    MAPPING_PROLOG              = 0x1,  
    MAPPING_EPILOG              = 0x2,  
    MAPPING_NO_INFO             = 0x4,  
    MAPPING_UNMAPPED_ADDRESS    = 0x8,  
    MAPPING_EXACT               = 0x10,  
    MAPPING_APPROXIMATE         = 0x20,  
} CorDebugMappingResult;  
```  
  
## <a name="members"></a><span data-ttu-id="c17c1-105">Členové</span><span class="sxs-lookup"><span data-stu-id="c17c1-105">Members</span></span>  
  
|<span data-ttu-id="c17c1-106">Člen</span><span class="sxs-lookup"><span data-stu-id="c17c1-106">Member</span></span>|<span data-ttu-id="c17c1-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c17c1-107">Description</span></span>|  
|------------|-----------------|  
|`MAPPING_PROLOG`|<span data-ttu-id="c17c1-108">Nativní kód je v prologu, takže IP má hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="c17c1-108">The native code is in the prolog, so the value of the IP is 0.</span></span>|  
|`MAPPING_EPILOG`|<span data-ttu-id="c17c1-109">Nativní kód epilogu, probíhá, tedy hodnota IP adresu poslední instrukce metody.</span><span class="sxs-lookup"><span data-stu-id="c17c1-109">The native code is in an epilog, so the value of the IP is the address of the last instruction of the method.</span></span>|  
|`MAPPING_NO_INFO`|<span data-ttu-id="c17c1-110">Žádné informace o mapování je k dispozici pro metodu, aby IP adresa má hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="c17c1-110">No mapping information is available for the method, so the value of the IP is 0.</span></span>|  
|`MAPPING_UNMAPPED_ADDRESS`|<span data-ttu-id="c17c1-111">Přestože jsou informace o mapování metody, aktuální adresu nelze mapovat na kód Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="c17c1-111">Although there is mapping information for the method, the current address cannot be mapped to Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="c17c1-112">IP adresa hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="c17c1-112">The value of the IP is 0.</span></span>|  
|`MAPPING_EXACT`|<span data-ttu-id="c17c1-113">Metoda mapuje přesně na kód jazyka MSIL nebo byl interpretován rámce, tak hodnota IP adresy je přesné.</span><span class="sxs-lookup"><span data-stu-id="c17c1-113">Either the method maps exactly to MSIL code or the frame has been interpreted, so the value of the IP is accurate.</span></span>|  
|`MAPPING_APPROXIMATE`|<span data-ttu-id="c17c1-114">Metoda byl úspěšně namapován, ale hodnota IP adresa může být přibližné.</span><span class="sxs-lookup"><span data-stu-id="c17c1-114">The method was successfully mapped, but the value of the IP may be approximate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c17c1-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c17c1-115">Remarks</span></span>  
 <span data-ttu-id="c17c1-116">Můžete použít [icordebugilframe::getip –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md) metodu k získání hodnoty ukazatele na instrukci.</span><span class="sxs-lookup"><span data-stu-id="c17c1-116">You can use the [ICorDebugILFrame::GetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md) method to obtain the value of the instruction pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c17c1-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c17c1-117">Requirements</span></span>  
 <span data-ttu-id="c17c1-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c17c1-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c17c1-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c17c1-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c17c1-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c17c1-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c17c1-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c17c1-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c17c1-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c17c1-122">See also</span></span>

- [<span data-ttu-id="c17c1-123">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="c17c1-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
