---
title: CLRDataEnumMemoryFlags – výčet
ms.date: 03/30/2017
api_name:
- CLRDataEnumMemoryFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLRDataEnumMemoryFlags
helpviewer_keywords:
- CLRDataEnumMemoryFlags enumeration [.NET Framework debugging]
ms.assetid: e249f9fc-e24a-4506-903c-92781f6eab7c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a19c6f22ee9fbe7eb1019a0b799d63e4ee650e98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406816"
---
# <a name="clrdataenummemoryflags-enumeration"></a><span data-ttu-id="1e139-102">CLRDataEnumMemoryFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="1e139-102">CLRDataEnumMemoryFlags Enumeration</span></span>
<span data-ttu-id="1e139-103">Určuje, které oblasti paměti volání [iclrdataenummemoryregions::enummemoryregions –](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) metoda by měla obsahovat.</span><span class="sxs-lookup"><span data-stu-id="1e139-103">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e139-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e139-104">Syntax</span></span>  
  
```  
typedef enum CLRDataEnumMemoryFlags {  
    CLRDATA_ENUM_MEM_DEFAULT  = 0x0,  
    CLRDATA_ENUM_MEM_MINI     = CLRDATA_ENUM_MEM_DEFAULT,  
    CLRDATA_ENUM_MEM_HEAP     = 0x1  
} CLRDataEnumMemoryFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="1e139-105">Členové</span><span class="sxs-lookup"><span data-stu-id="1e139-105">Members</span></span>  
  
|<span data-ttu-id="1e139-106">Člen</span><span class="sxs-lookup"><span data-stu-id="1e139-106">Member</span></span>|<span data-ttu-id="1e139-107">Popis</span><span class="sxs-lookup"><span data-stu-id="1e139-107">Description</span></span>|  
|------------|-----------------|  
|`CLRDATA_ENUM_MEM_DEFAULT`|<span data-ttu-id="1e139-108">Minimální výpis, tedy zhuštěných výpisu stavu paměti.</span><span class="sxs-lookup"><span data-stu-id="1e139-108">A minidump, that is, a sparse memory dump.</span></span>|  
|`CLRDATA_ENUM_MEM_HEAP`|<span data-ttu-id="1e139-109">Výpis úplné haldy.</span><span class="sxs-lookup"><span data-stu-id="1e139-109">A full heap dump.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1e139-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1e139-110">Requirements</span></span>  
 <span data-ttu-id="1e139-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e139-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e139-112">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="1e139-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="1e139-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1e139-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e139-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e139-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e139-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="1e139-115">See Also</span></span>  
 [<span data-ttu-id="1e139-116">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="1e139-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
