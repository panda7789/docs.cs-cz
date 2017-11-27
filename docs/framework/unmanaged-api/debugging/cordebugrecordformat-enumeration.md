---
title: "Výčet CorDebugRecordFormat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugRecordFormat
api_location: mscordbi.dll
api_type: COM
ms.assetid: d680c1c0-16ab-4ccc-9444-39cf8e0e05ee
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c2f8397382dde061078a0d96114420f1c5f48669
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugrecordformat-enumeration"></a><span data-ttu-id="1060a-102">Výčet CorDebugRecordFormat</span><span class="sxs-lookup"><span data-stu-id="1060a-102">CorDebugRecordFormat Enumeration</span></span>
<span data-ttu-id="1060a-103">Popisuje formát dat v bajtové pole obsahující informace o události ladění nativního výjimka.</span><span class="sxs-lookup"><span data-stu-id="1060a-103">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1060a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1060a-104">Syntax</span></span>  
  
```  
typedef enum CorDebugRecordFormat {  
    FORMAT_WINDOWS_EXCEPTIONRECORD32 = 1,  
    FORMAT_WINDOWS_EXCEPTIONRECORD64 = 2,  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="1060a-105">Členové</span><span class="sxs-lookup"><span data-stu-id="1060a-105">Members</span></span>  
  
|<span data-ttu-id="1060a-106">Člen</span><span class="sxs-lookup"><span data-stu-id="1060a-106">Member</span></span>|<span data-ttu-id="1060a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="1060a-107">Description</span></span>|  
|------------|-----------------|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD32`|<span data-ttu-id="1060a-108">Data je záznam 32bitová verze Windows výjimky.</span><span class="sxs-lookup"><span data-stu-id="1060a-108">The data is a 32-bit Windows exception record.</span></span>|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD64`|<span data-ttu-id="1060a-109">Data je záznam 64bitová verze Windows výjimky.</span><span class="sxs-lookup"><span data-stu-id="1060a-109">The data is a 64-bit Windows exception record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1060a-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1060a-110">Remarks</span></span>  
 <span data-ttu-id="1060a-111">Členem `CorDebugRecordFormat` předaný výčet [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) metoda udávajících formát bajtového pole v jeho `pRecord` argument.</span><span class="sxs-lookup"><span data-stu-id="1060a-111">A member of the `CorDebugRecordFormat` enumeration is passed to the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method to indicate the format of the byte array in its `pRecord` argument.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1060a-112">Tento výčet je určena pro použití v rozhraní .NET nativní ladění pouze scénáře.</span><span class="sxs-lookup"><span data-stu-id="1060a-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1060a-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1060a-113">Requirements</span></span>  
 <span data-ttu-id="1060a-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1060a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1060a-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1060a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1060a-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1060a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1060a-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1060a-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1060a-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="1060a-118">See Also</span></span>  
 [<span data-ttu-id="1060a-119">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="1060a-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
