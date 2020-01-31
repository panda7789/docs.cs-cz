---
title: LogSwitchCallReason – výčet
ms.date: 03/30/2017
api_name:
- LogSwitchCallReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LogSwitchCallReason
helpviewer_keywords:
- LogSwitchCallReason enumeration [.NET Framework debugging]
ms.assetid: 5bbb8d1b-bbc4-47b0-b1b1-2d54cc0be291
topic_type:
- apiref
ms.openlocfilehash: 29781666c106755f96f945325e3a8953bf93b211
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790350"
---
# <a name="logswitchcallreason-enumeration"></a><span data-ttu-id="89236-102">LogSwitchCallReason – výčet</span><span class="sxs-lookup"><span data-stu-id="89236-102">LogSwitchCallReason Enumeration</span></span>
<span data-ttu-id="89236-103">Určuje operaci, která byla provedena na přepínači ladění/trasování.</span><span class="sxs-lookup"><span data-stu-id="89236-103">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89236-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89236-104">Syntax</span></span>  
  
```cpp  
typedef enum LogSwitchCallReason {  
    SWITCH_CREATE,  
    SWITCH_MODIFY,  
    SWITCH_DELETE  
} LogSwitchCallReason;  
```  
  
## <a name="members"></a><span data-ttu-id="89236-105">Členové</span><span class="sxs-lookup"><span data-stu-id="89236-105">Members</span></span>  
  
|<span data-ttu-id="89236-106">Člen</span><span class="sxs-lookup"><span data-stu-id="89236-106">Member</span></span>|<span data-ttu-id="89236-107">Popis</span><span class="sxs-lookup"><span data-stu-id="89236-107">Description</span></span>|  
|------------|-----------------|  
|`SWITCH_CREATE`|<span data-ttu-id="89236-108">Byl vytvořen přepínač ladění/trasování.</span><span class="sxs-lookup"><span data-stu-id="89236-108">A debugging/tracing switch was created.</span></span>|  
|`SWITCH_MODIFY`|<span data-ttu-id="89236-109">Přepínač ladění/trasování byl změněn.</span><span class="sxs-lookup"><span data-stu-id="89236-109">A debugging/tracing switch was modified.</span></span>|  
|`SWITCH_DELETE`|<span data-ttu-id="89236-110">Přepínač ladění/trasování byl odstraněn.</span><span class="sxs-lookup"><span data-stu-id="89236-110">A debugging/tracing switch was deleted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="89236-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="89236-111">Requirements</span></span>  
 <span data-ttu-id="89236-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89236-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89236-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="89236-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89236-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="89236-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89236-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89236-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89236-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89236-116">See also</span></span>

- [<span data-ttu-id="89236-117">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="89236-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
