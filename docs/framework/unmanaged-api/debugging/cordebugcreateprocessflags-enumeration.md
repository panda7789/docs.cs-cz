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
ms.openlocfilehash: 83cee30ed9831accb96de17768f63e7f401908f0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495948"
---
# <a name="cordebugcreateprocessflags-enumeration"></a><span data-ttu-id="59614-102">CorDebugCreateProcessFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="59614-102">CorDebugCreateProcessFlags Enumeration</span></span>
<span data-ttu-id="59614-103">Poskytuje další možnosti ladění, které lze použít ve volání [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="59614-103">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59614-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59614-104">Syntax</span></span>  
  
```  
typedef enum CorDebugCreateProcessFlags {  
    DEBUG_NO_SPECIAL_OPTIONS    = 0x0000  
} CorDebugCreateProcessFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="59614-105">Členové</span><span class="sxs-lookup"><span data-stu-id="59614-105">Members</span></span>  
  
|<span data-ttu-id="59614-106">Člen</span><span class="sxs-lookup"><span data-stu-id="59614-106">Member</span></span>|<span data-ttu-id="59614-107">Popis</span><span class="sxs-lookup"><span data-stu-id="59614-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_NO_SPECIAL_OPTIONS`|<span data-ttu-id="59614-108">Nejsou nastaveny žádné speciální možnosti.</span><span class="sxs-lookup"><span data-stu-id="59614-108">No special options are set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="59614-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="59614-109">Requirements</span></span>  
 <span data-ttu-id="59614-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59614-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59614-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="59614-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59614-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59614-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59614-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59614-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59614-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="59614-114">See also</span></span>
- [<span data-ttu-id="59614-115">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="59614-115">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
