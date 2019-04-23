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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7eadb595eb62b4f1a9dcc888225cbb7454119c7c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59198488"
---
# <a name="logswitchcallreason-enumeration"></a><span data-ttu-id="c8f01-102">LogSwitchCallReason – výčet</span><span class="sxs-lookup"><span data-stu-id="c8f01-102">LogSwitchCallReason Enumeration</span></span>
<span data-ttu-id="c8f01-103">Určuje operaci, která byla provedena na přepínači ladění a trasování.</span><span class="sxs-lookup"><span data-stu-id="c8f01-103">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8f01-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8f01-104">Syntax</span></span>  
  
```  
typedef enum LogSwitchCallReason {  
    SWITCH_CREATE,  
    SWITCH_MODIFY,  
    SWITCH_DELETE  
} LogSwitchCallReason;  
```  
  
## <a name="members"></a><span data-ttu-id="c8f01-105">Členové</span><span class="sxs-lookup"><span data-stu-id="c8f01-105">Members</span></span>  
  
|<span data-ttu-id="c8f01-106">Člen</span><span class="sxs-lookup"><span data-stu-id="c8f01-106">Member</span></span>|<span data-ttu-id="c8f01-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c8f01-107">Description</span></span>|  
|------------|-----------------|  
|`SWITCH_CREATE`|<span data-ttu-id="c8f01-108">Ladění a trasování přepínače byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="c8f01-108">A debugging/tracing switch was created.</span></span>|  
|`SWITCH_MODIFY`|<span data-ttu-id="c8f01-109">Ladění a trasování přepínače byla změněna.</span><span class="sxs-lookup"><span data-stu-id="c8f01-109">A debugging/tracing switch was modified.</span></span>|  
|`SWITCH_DELETE`|<span data-ttu-id="c8f01-110">Ladění a trasování přepínače byl odstraněn.</span><span class="sxs-lookup"><span data-stu-id="c8f01-110">A debugging/tracing switch was deleted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c8f01-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c8f01-111">Requirements</span></span>  
 <span data-ttu-id="c8f01-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8f01-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8f01-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c8f01-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8f01-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8f01-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8f01-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8f01-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8f01-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c8f01-116">See also</span></span>

- [<span data-ttu-id="c8f01-117">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="c8f01-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
