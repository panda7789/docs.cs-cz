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
ms.openlocfilehash: adb13688791cd7d8f467780da1895d4f9fe6e990
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739641"
---
# <a name="cordebugrecordformat-enumeration"></a><span data-ttu-id="39d84-102">Výčet CorDebugRecordFormat</span><span class="sxs-lookup"><span data-stu-id="39d84-102">CorDebugRecordFormat Enumeration</span></span>
<span data-ttu-id="39d84-103">Popisuje formát dat v bajtové pole, která obsahuje informace o události ladění nativní výjimka.</span><span class="sxs-lookup"><span data-stu-id="39d84-103">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39d84-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39d84-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugRecordFormat {  
    FORMAT_WINDOWS_EXCEPTIONRECORD32 = 1,  
    FORMAT_WINDOWS_EXCEPTIONRECORD64 = 2,  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="39d84-105">Členové</span><span class="sxs-lookup"><span data-stu-id="39d84-105">Members</span></span>  
  
|<span data-ttu-id="39d84-106">Člen</span><span class="sxs-lookup"><span data-stu-id="39d84-106">Member</span></span>|<span data-ttu-id="39d84-107">Popis</span><span class="sxs-lookup"><span data-stu-id="39d84-107">Description</span></span>|  
|------------|-----------------|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD32`|<span data-ttu-id="39d84-108">Data jsou výjimky záznam 32bitová verze Windows.</span><span class="sxs-lookup"><span data-stu-id="39d84-108">The data is a 32-bit Windows exception record.</span></span>|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD64`|<span data-ttu-id="39d84-109">Data jsou záznam výjimky Windows 64-bit.</span><span class="sxs-lookup"><span data-stu-id="39d84-109">The data is a 64-bit Windows exception record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39d84-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="39d84-110">Remarks</span></span>  
 <span data-ttu-id="39d84-111">Člen `CorDebugRecordFormat` výčtu je předána [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) indikace formátu bajtového pole v jeho `pRecord` argument.</span><span class="sxs-lookup"><span data-stu-id="39d84-111">A member of the `CorDebugRecordFormat` enumeration is passed to the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method to indicate the format of the byte array in its `pRecord` argument.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="39d84-112">Tento výčet je určena pro použití v .NET Native ladění pouze scénáře.</span><span class="sxs-lookup"><span data-stu-id="39d84-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39d84-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="39d84-113">Requirements</span></span>  
 <span data-ttu-id="39d84-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39d84-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39d84-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="39d84-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39d84-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39d84-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39d84-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39d84-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39d84-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="39d84-118">See also</span></span>

- [<span data-ttu-id="39d84-119">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="39d84-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
