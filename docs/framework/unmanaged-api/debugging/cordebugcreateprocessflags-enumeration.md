---
title: "CorDebugCreateProcessFlags – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugCreateProcessFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugCreateProcessFlags
helpviewer_keywords: CorDebugCreateProcessFlags enumeration [.NET Framework debugging]
ms.assetid: e709acce-6a17-4346-b38a-467dba567358
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e35aa2656a1e950cead94480eb06cde96e4c811
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugcreateprocessflags-enumeration"></a><span data-ttu-id="8ecf1-102">CorDebugCreateProcessFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="8ecf1-102">CorDebugCreateProcessFlags Enumeration</span></span>
<span data-ttu-id="8ecf1-103">Poskytuje další možnosti ladění, které mohou být používány volání [icordebug::CreateProcess –](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="8ecf1-103">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ecf1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ecf1-104">Syntax</span></span>  
  
```  
typedef enum CorDebugCreateProcessFlags {  
    DEBUG_NO_SPECIAL_OPTIONS    = 0x0000  
} CorDebugCreateProcessFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="8ecf1-105">Členové</span><span class="sxs-lookup"><span data-stu-id="8ecf1-105">Members</span></span>  
  
|<span data-ttu-id="8ecf1-106">Člen</span><span class="sxs-lookup"><span data-stu-id="8ecf1-106">Member</span></span>|<span data-ttu-id="8ecf1-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8ecf1-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_NO_SPECIAL_OPTIONS`|<span data-ttu-id="8ecf1-108">Nejsou nastaveny žádné speciální možnosti.</span><span class="sxs-lookup"><span data-stu-id="8ecf1-108">No special options are set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8ecf1-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8ecf1-109">Requirements</span></span>  
 <span data-ttu-id="8ecf1-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ecf1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ecf1-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ecf1-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ecf1-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ecf1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ecf1-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ecf1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ecf1-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ecf1-114">See Also</span></span>  
 [<span data-ttu-id="8ecf1-115">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="8ecf1-115">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
