---
title: Výčet CorDebugRecordFormat
ms.date: 03/30/2017
api_name:
- CorDebugRecordFormat
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: d680c1c0-16ab-4ccc-9444-39cf8e0e05ee
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e6ed7d25593f9dd5d5d01f8c06024dcf8acfcfea
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916475"
---
# <a name="cordebugrecordformat-enumeration"></a><span data-ttu-id="2f069-102">Výčet CorDebugRecordFormat</span><span class="sxs-lookup"><span data-stu-id="2f069-102">CorDebugRecordFormat Enumeration</span></span>
<span data-ttu-id="2f069-103">Popisuje formát dat v bajtovém poli, které obsahuje informace o nativní události ladění výjimky.</span><span class="sxs-lookup"><span data-stu-id="2f069-103">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f069-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f069-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugRecordFormat {  
    FORMAT_WINDOWS_EXCEPTIONRECORD32 = 1,  
    FORMAT_WINDOWS_EXCEPTIONRECORD64 = 2,  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="2f069-105">Členové</span><span class="sxs-lookup"><span data-stu-id="2f069-105">Members</span></span>  
  
|<span data-ttu-id="2f069-106">Člen</span><span class="sxs-lookup"><span data-stu-id="2f069-106">Member</span></span>|<span data-ttu-id="2f069-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2f069-107">Description</span></span>|  
|------------|-----------------|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD32`|<span data-ttu-id="2f069-108">Data jsou 32 záznam výjimky systému Windows.</span><span class="sxs-lookup"><span data-stu-id="2f069-108">The data is a 32-bit Windows exception record.</span></span>|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD64`|<span data-ttu-id="2f069-109">Data jsou 64 záznam výjimky systému Windows.</span><span class="sxs-lookup"><span data-stu-id="2f069-109">The data is a 64-bit Windows exception record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f069-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2f069-110">Remarks</span></span>  
 <span data-ttu-id="2f069-111">Člen `CorDebugRecordFormat` výčtu je předán metodě [DecodeEvent –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) k určení formátu `pRecord` bajtového pole v argumentu.</span><span class="sxs-lookup"><span data-stu-id="2f069-111">A member of the `CorDebugRecordFormat` enumeration is passed to the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method to indicate the format of the byte array in its `pRecord` argument.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2f069-112">Tento výčet je určený pro použití pouze v .NET Nativech scénářích ladění.</span><span class="sxs-lookup"><span data-stu-id="2f069-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f069-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2f069-113">Requirements</span></span>  
 <span data-ttu-id="2f069-114">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f069-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f069-115">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2f069-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f069-116">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f069-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f069-117">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f069-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f069-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2f069-118">See also</span></span>

- [<span data-ttu-id="2f069-119">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="2f069-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
