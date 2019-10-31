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
ms.openlocfilehash: 769e63ac6e23ae0264b79a1cd8d6e3cc1ac5a744
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132409"
---
# <a name="clrdataenummemoryflags-enumeration"></a><span data-ttu-id="69295-102">CLRDataEnumMemoryFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="69295-102">CLRDataEnumMemoryFlags Enumeration</span></span>
<span data-ttu-id="69295-103">Určuje, které oblasti paměti musí volání metody [ICLRDataEnumMemoryRegions –:: EnumMemoryRegions –](iclrdataenummemoryregions-enummemoryregions-method.md) zahrnovat.</span><span class="sxs-lookup"><span data-stu-id="69295-103">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69295-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69295-104">Syntax</span></span>  
  
```cpp  
typedef enum CLRDataEnumMemoryFlags {  
    CLRDATA_ENUM_MEM_DEFAULT  = 0x0,  
    CLRDATA_ENUM_MEM_MINI     = CLRDATA_ENUM_MEM_DEFAULT,  
    CLRDATA_ENUM_MEM_HEAP     = 0x1  
} CLRDataEnumMemoryFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="69295-105">Členové</span><span class="sxs-lookup"><span data-stu-id="69295-105">Members</span></span>  
  
|<span data-ttu-id="69295-106">Člen</span><span class="sxs-lookup"><span data-stu-id="69295-106">Member</span></span>|<span data-ttu-id="69295-107">Popis</span><span class="sxs-lookup"><span data-stu-id="69295-107">Description</span></span>|  
|------------|-----------------|  
|`CLRDATA_ENUM_MEM_DEFAULT`|<span data-ttu-id="69295-108">S minimálním výpisem, to znamená zhuštěný výpis paměti.</span><span class="sxs-lookup"><span data-stu-id="69295-108">A minidump, that is, a sparse memory dump.</span></span>|  
|`CLRDATA_ENUM_MEM_HEAP`|<span data-ttu-id="69295-109">Úplný výpis paměti haldy.</span><span class="sxs-lookup"><span data-stu-id="69295-109">A full heap dump.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="69295-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="69295-110">Requirements</span></span>  
 <span data-ttu-id="69295-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69295-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69295-112">**Hlavička:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="69295-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="69295-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="69295-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69295-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69295-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69295-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69295-115">See also</span></span>

- [<span data-ttu-id="69295-116">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="69295-116">Debugging Enumerations</span></span>](debugging-enumerations.md)
