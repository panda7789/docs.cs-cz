---
title: CorDebugCreateProcessFlags – výčet
ms.date: 03/30/2017
api_name:
- CorDebugCreateProcessFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugCreateProcessFlags
helpviewer_keywords:
- CorDebugCreateProcessFlags enumeration [.NET Framework debugging]
ms.assetid: e709acce-6a17-4346-b38a-467dba567358
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae3ba480e208762f5a80f9f1b78dd008f02b6df4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089374"
---
# <a name="cordebugcreateprocessflags-enumeration"></a><span data-ttu-id="a4e1c-102">CorDebugCreateProcessFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="a4e1c-102">CorDebugCreateProcessFlags Enumeration</span></span>
<span data-ttu-id="a4e1c-103">Poskytuje další možnosti ladění, které lze použít ve volání [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="a4e1c-103">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4e1c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4e1c-104">Syntax</span></span>  
  
```  
typedef enum CorDebugCreateProcessFlags {  
    DEBUG_NO_SPECIAL_OPTIONS    = 0x0000  
} CorDebugCreateProcessFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="a4e1c-105">Členové</span><span class="sxs-lookup"><span data-stu-id="a4e1c-105">Members</span></span>  
  
|<span data-ttu-id="a4e1c-106">Člen</span><span class="sxs-lookup"><span data-stu-id="a4e1c-106">Member</span></span>|<span data-ttu-id="a4e1c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a4e1c-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_NO_SPECIAL_OPTIONS`|<span data-ttu-id="a4e1c-108">Nejsou nastaveny žádné speciální možnosti.</span><span class="sxs-lookup"><span data-stu-id="a4e1c-108">No special options are set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a4e1c-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a4e1c-109">Requirements</span></span>  
 <span data-ttu-id="a4e1c-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4e1c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4e1c-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a4e1c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a4e1c-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a4e1c-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="a4e1c-113">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="a4e1c-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a4e1c-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a4e1c-114">See also</span></span>

- [<span data-ttu-id="a4e1c-115">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="a4e1c-115">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
