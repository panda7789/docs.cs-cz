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
ms.openlocfilehash: 67b85917be590bdba7ed3f10972ad39b731dbcdd
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274247"
---
# <a name="clrdataenummemoryflags-enumeration"></a><span data-ttu-id="83994-102">CLRDataEnumMemoryFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="83994-102">CLRDataEnumMemoryFlags Enumeration</span></span>
<span data-ttu-id="83994-103">Určuje, které oblasti paměti musí volání metody [ICLRDataEnumMemoryRegions –:: EnumMemoryRegions –](iclrdataenummemoryregions-enummemoryregions-method.md) zahrnovat.</span><span class="sxs-lookup"><span data-stu-id="83994-103">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83994-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83994-104">Syntax</span></span>  
  
```cpp  
typedef enum CLRDataEnumMemoryFlags {  
    CLRDATA_ENUM_MEM_DEFAULT  = 0x0,  
    CLRDATA_ENUM_MEM_MINI     = CLRDATA_ENUM_MEM_DEFAULT,  
    CLRDATA_ENUM_MEM_HEAP     = 0x1  
} CLRDataEnumMemoryFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="83994-105">Členové</span><span class="sxs-lookup"><span data-stu-id="83994-105">Members</span></span>  
  
|<span data-ttu-id="83994-106">Člen</span><span class="sxs-lookup"><span data-stu-id="83994-106">Member</span></span>|<span data-ttu-id="83994-107">Popis</span><span class="sxs-lookup"><span data-stu-id="83994-107">Description</span></span>|  
|------------|-----------------|  
|`CLRDATA_ENUM_MEM_DEFAULT`|<span data-ttu-id="83994-108">S minimálním výpisem, to znamená zhuštěný výpis paměti.</span><span class="sxs-lookup"><span data-stu-id="83994-108">A minidump, that is, a sparse memory dump.</span></span>|  
|`CLRDATA_ENUM_MEM_HEAP`|<span data-ttu-id="83994-109">Úplný výpis paměti haldy.</span><span class="sxs-lookup"><span data-stu-id="83994-109">A full heap dump.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="83994-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="83994-110">Requirements</span></span>  
 <span data-ttu-id="83994-111">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83994-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83994-112">**Hlaviček** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="83994-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="83994-113">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83994-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83994-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83994-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83994-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="83994-115">See also</span></span>

- [<span data-ttu-id="83994-116">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="83994-116">Debugging Enumerations</span></span>](debugging-enumerations.md)
